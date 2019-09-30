###java配置
~~~java
@EnableSwagger2
@Configuration
public class Swagger2Config {

    /**
     * Swagger2参数详解
     *
     * @Api：修饰整个类，描述Controller的作用
     * @ApiOperation：描述一个类的一个方法，或者说一个接口
     * @ApiParam：单个参数描述@ApiModel：用对象来接收参数
     * @ApiProperty：用对象接收参数时，描述对象的一个字段
     * @ApiResponse：HTTP响应其中1个描述
     * @ApiResponses：HTTP响应整体描述
     * @ApiIgnore：使用该注解忽略这个API
     * @ApiError：发生错误返回的信息
     * @ApiImplicitParam：一个请求参数
     * @ApiImplicitParams：多个请求参数
     */

    @Bean
    public Docket createRestApi() {
        return new Docket(DocumentationType.SWAGGER_2)
                .apiInfo(apiInfo())
                .select()
                //为当前包路径
                .apis(RequestHandlerSelectors.basePackage("com.hege.demo.controller"))
                .paths(PathSelectors.any())
                .build();
    }

    //构建 api文档的详细信息函数
    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
                //页面标题
                .title("demo服务接口开发文档")
                //创建人
                .contact(new Contact("Maple", "", "1150640979@qq.com"))
                //版本号
                .version("1.0")
                //描述
                .description("demo服务接口开发文档")
                .build();
    }
}
~~~

请求地址：[http://127.0.0.1:8088/swagger-ui.html](请求地址：[http://127.0.0.1:8088/swagger-ui.html#/]())