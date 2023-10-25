# Q-A
it is used to remember how to answer some questions

## Annoations in Java
@Named - normally it is used to name a beans that have the same interface, so that when we want to inject the bean, we can use the name as reference.
@Named("accountDetail")
@Named("accountSearch")
@Named("applicationConfig")
@Stateless - bean is not state bean
@PersistenceContext 
it is for entitymanager in JPA, not sprint annoation, normally we can not use autowired to replace it, since we need to create EM for each thread, but autowired only have one re-used EM.
@Inject
@RequestScoped/@ViewScoped/@ApplicationScoped/@ConversationScoped

@UserToken("domo")
@Resource(name = "domo-api-uri", lookup = "app/domo-api-uri")


@PostConstruct - aspect?
@PreDestroy

@Qualifier like a name
@Retention(RUNTIME) - annoation is existed in RUNTIME, CLASS is build, source, only in source code
@Target({ FIELD, METHOD }) -- annoation's target, can be used for

@FacesConfig - not know it, it should be a config for faces(views)???

@BeforeEach - junit testm it should be run before each case
@Test - test case in Junit
