# File upload

## Multipart FormData

### Multipart FormData 정의

* Header의 Content-Type을 `multipart/form-data`로 설정 하는것을 뜻한다.
* `multipart/form-data`는 파일 업로드를 위한 데이터 타입이다.

### Multipart FormData 사용

```java
@PostMapping(consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
    @ResponseStatus(HttpStatus.CREATED)
    public void add(@ModelAttribute ProductCreateDto reqBody){
        addProductService.add(reqBody);
    }
```

* 위의 예제와 같이 consumes 속성을 `MediaType.MULTIPART_FORM_DATA_VALUE`로 설정하고 `@ModelAttribute`를 사용하여 데이터를 받는다.

### Multipart FormData 사용하는 이유?

* 모든 문자를 인코딩하지 않음을 명시한다.
이 방식은 form 요소가 파일이나 이미지를 서버로 전송할 때 주로 사용한다.

## Separation of Concerns

### Separation of Concerns 정의

* 파일 업로드 역시 인프라를 이용하는 것이기 때문에 역할을 분리해야 한다.

### Separation of Concerns 의 실제 구현

```java
    public void add(ProductCreateDto createDto) {

        MultipartFile image = createDto.getImage();
        if (image == null || image.isEmpty()) {
            throw new ImageNotFoundException();
        }

        String imagePath;

        try {
            imagePath = imageStorage.autoSave(image.getBytes());
        } catch (IOException e) {
            throw new ImageNotFoundException();
        }

        var product = new Product(new ProductId(), createDto.getName(), imagePath, createDto.getPrice());
        productRepository.save(product);
    }
```

* 위와 같이 이미지 저장을 담당하는 `ImageStorage`를 만들어 역할을 분리한다.
* `ImageStorage`는 `MultipartFile`을 받아 이미지를 저장하고 저장된 이미지의 경로를 반환한다.
* `ImageStorage`는 `ImageNotFoundException`을 발생시킬 수 있다.

### Separation of Concerns 의 테스트 구현

```java
    @Test
    @DisplayName("POST /products")
    void add() throws Exception {
        String filename = "src/test/resources/files/test.jpg";

        MockMultipartFile file = new MockMultipartFile(
                "image", "test.jpg", "image/jpeg",
                new FileInputStream(filename));

        var reqBody = new ProductCreateDto("product-name", file, 100_000L);

        mockMvc.perform(MockMvcRequestBuilders.multipart("/products")
                        .file(file)
                        .param("name", reqBody.getName())
                        .param("price", String.valueOf(reqBody.getPrice())))
                .andExpect(MockMvcResultMatchers.status().isCreated());
    }
```

* 위와 같이 `MockMultipartFile`을 사용하여 form 에 들어갈 수 있는 형태로 만들어준다.
* `MockMvcRequestBuilders.multipart`를 사용하여 `multipart/form-data`를 사용하는 것을 명시한다. (Post 가 전제되어 있다.)

## Cloudinary

* Cloudinary 는 이미지를 저장하고 관리하는 서비스이다.
* Cloudinary 를 사용하면 파일을 관리하는 불편함을 줄일 수 있다.
* Cloudinary 는 무료로 사용할 수 있다
* Cloudinary 의 관리 서비스를 통해 파일 저장 전략(백업, 분산, ...) 을 신경쓰지 않아도 된다.
