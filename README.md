# Q-A
it is used to remember how to answer some questions

## Annoations in Java
### @Named 
 normally it is used to name a beans that have the same interface, so that when we want to inject the bean, we can use the name as reference.
@Named("accountDetail")
@Named("accountSearch")
@Named("applicationConfig")
### @Stateless - bean is not state bean
### @PersistenceContext 
it is for entitymanager in JPA, not sprint annoation, normally we can not use autowired to replace it, since we need to create EM for each thread, but autowired only have one re-used EM.
### @Inject
### @RequestScoped/@ViewScoped/@ApplicationScoped/@ConversationScoped

### @UserToken("domo")
### @Resource(name = "domo-api-uri", lookup = "app/domo-api-uri")


### @PostConstruct - aspect?
### @PreDestroy

#### @Qualifier like a name
#### @Retention(RUNTIME) - annoation is existed in RUNTIME, CLASS is build, source, only in source code
### @Target({ FIELD, METHOD }) -- annoation's target, can be used for

### @FacesConfig - not know it, it should be a config for faces(views)???

### @BeforeEach - junit testm it should be run before each case
### @Test - test case in Junit

## Springboot Annoation
### @requestMapping(value = '/hello', method= RequestMethod.GET)
### RestController/Controller
### @CrossOrigin
### @Validated
~~~
getParts(			
	@RequestParam(value="part_num",required = true)
	@NotNull(message ="The part_num parameter was not supplied with a value.")
	Size(min = 1,message ="The part_num parameter was not supplied with a value.")
	String partNum,
												
	@RequestParam(value="source",required = false) 
	@Size(min = 0,max = 10,message ="Value for id parameter exceeds 10 characters")
	String source)
getPartByNum(			
	@PathVariable(value="part_num",required = true)
	@NotNull(message ="The part_num parameter was not supplied with a value.")
	@Size(min = 1,message ="The part_num parameter was not supplied with a value.")
	String partNum,
												
	@RequestParam(value="source",required = false) 
	@Size(min = 0,max = 10,message ="Value for id parameter exceeds 10 characters")
	String source) throws Exception
~~~

### @Repository for DAO
@Autowired
    protected JdbcTemplate jdbcTemplate;

### public class AuthenticationInterceptor implements HandlerInterceptor 

### add authorization and interceptor
~~~
@Configuration
public class RestfulWebConfig implements WebMvcConfigurer 
{
	@Bean
    public AuthenticationInterceptor authenticationInterceptor(){
        return new AuthenticationInterceptor();
    }
	
  @Override
  public void addInterceptors(InterceptorRegistry registry) {
    // 
    registry.addInterceptor(authenticationInterceptor())
    						.addPathPatterns("/**")
	    					.excludePathPatterns("/**/*.css", 
				            "/**/*.js", "/**/*.png", "/**/*.jpg", 
				            "/**/*.jpeg", "/**/*.gif", "/**/*.yaml");
  }
}
~~~
### Exception for controller
~~~
/**
 * Restful exception Handler

@ControllerAdvice
public class ApiExceptionHandler 

	@ExceptionHandler(MissingServletRequestParameterException.class)
	@ResponseBody
	public ResponseEntity<ErrorResponse> handleMissingParams(MissingServletRequestParameterException e) 
	{
	    String name = e.getParameterName();
		logger.warn("MissingServletRequestParameterException " + name,e.getMessage());			
//		MissingScheduleException missingScheduleEx = null;//new MissingScheduleException();
		ErrorResponse errorResponse = new ErrorResponse();
		errorResponse.addErrorsItem(new Error().code(null).message(null));		
		ResponseEntity<ErrorResponse> responseEntity = new ResponseEntity<ErrorResponse>(errorResponse, HttpStatus.BAD_REQUEST);			
		return responseEntity;
	}
~~~
