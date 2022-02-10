# SPRING INITIALIZR
  https://start.spring.io/
  
  **Configurazione progetto:**
  
	  Project : Maven
	  Language: Java
	  Spring Boot: 2.5
	  Project Metadata:
	    - Group : com.rubrica
	    - Artifact: rubrica
	    - Name: rubrica
	    - Description: Training Rubrica
	    - Package name: com.rubrica.rubrica
	  Packaging: Jar
	  Java: 8
  
  **importare il progetto su ECLIPSE**
  
  **aggiungere queste dipendenze nel pom:**
  
  	  **spring web**
	  groupId: org.springframework.boot
	  artifactId: spring-boot-starter-web
	  **spring contex**
	  groupId: org.springframework
	  artifactId: spring-context   
	  **spring context support**
	  groupId: org.springframework
	  artifactId: spring-context-support  
	  **spring starter data jpa**
	  groupId: org.springframework.boot
	  artifactId: spring-boot-starter-data-jpa  
	  **spring data jpa**
	  groupId: org.springframework.data
	  artifactId: spring-data-jpa  
	  **mapstruct**
	  groupId: org.mapstruct
	  artifactId: mapstruct
	  version: 1.3.1.Final  
	  **spring starter validation**
	  groupId: org.springframework.boot
	  artifactId: spring-boot-starter-validation

# CONFIGURARE CONNESSIONE AL DB SU ECLIPSE

  **Adding MySQL connector jar file in Eclipse** (https://www.tutorialsfield.com/how-to-connect-mysql-database-in-java-using-eclipse/)

  -	creare un nuovo .properties : **application-dev.properties**
  -	inserire nel nuovo properties:

	    server.port=8080
	    spring.jpa.hibernate.ddl-auto=none
	    spring.datasource.url=jdbc:mysql://localhost:3306/rubrica
	    spring.datasource.username=root
	    spring.datasource.password=root
	    spring.datasource.driver-class-name=com.mysql.jdbc.Driver
	    spring.jpa.show-sql: true
  
  **Annotare la classe di run dell’applicazione** (contrassegnata dall’annotazione SpringBootApplication) **con le seguenti annotazioni 
  per far si che il repository venga riconosciuto** 
  
  	@EnableSwagger2
	@ComponentScan("[nome package padre del package in cui risiede il repository]")
  
# Creare un run JavaApplication :
  -	Tasto destro sul progetto -> Run Us -> Run Configuration
  -	Dal menu di sinistra scegliere Java Application e fare click destro New Configuration
  -	Tramite Browse scegliere il progetto e la main class associata al progetto
  -	Spostarsi nel tab Argument e nel riquadro VM Arguments inserire l’istruzione **-Dspring.profiles.active=dev**
   
# IMPOSTARE .JAR  DEL SERVER
  tasto dx sul progetto-> build Path -> configure build path -> sotto il tab Libreries importare il jar [**mysql-connector-java-8.0.26.jar**]

# CONFIGURARE SWAGGER: 
  **nella classe del main** (contrassegnata dall’annotazione SpringBootApplication) **inserire il metodo**
  
	@Bean
	public Docket api() {
		return new Docket(DocumentationType.SWAGGER_2)
			.select()
			.apis(RequestHandlerSelectors.basePackage("com.accenture.rubrica.controller"))
			.paths(PathSelectors.any())
			.build()
			.pathMapping("/");

  **Nel pom inserire le dipendenze:**

    groupId: io.springfox
    artifactId: springfox-swagger2
    version: 3.0.0
    groupId: io.springfox
    artifactId: springfox-swagger-ui
    version: 2.9.2
  
# CREAZIONE STRUTTURA PROGETTO: 
  -	classi **Controller** (di tipo RestController inserito in un apposito package **.controller**), annotate con **@RestController**
  -	classi  **Facade** (inserito in un apposito package **.facade**),  annotate con **@Component**
  -	classi  **Service** (inserito in un apposito package **.service**) annotate con  **@Service**
  -	classi  **Repository** (inserito in un apposito package **.repository**) annotate con **@Repository**
	
		ES.
		      @Repository
		      public interface [nomeClasseEntity]Repository extends JpaRepository<[ClasseEntity], [chiaveClasseEntity]> {}
  - classi  **Entity** (inserito in un apposito package **.entity**)  annotate con  **@Entity**

# CREAZIONE ENTITY JAVA 
  GUIDA https://www.baeldung.com/jpa-entities
  
# CREAZIONE REPOSITORY ASSOCIATI ALLE ENTITY 
  UN REPOSITORY PER OGNI ENTITY
 
# JPA @Query 
  https://www.baeldung.com/spring-data-jpa-query
  
# Nel controller utilizzare le  ResponseEntity
  https://www.baeldung.com/spring-response-entity


