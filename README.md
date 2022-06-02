<h1>Microservices cloud-config</h1>

<ul class="list-group">
    <li class="list-group-item">1. create microservice -> config server & dev tools</li>
    <br>
    <li class="list-group-item">2. annotate main file with @EnableConfigServer</li>
    <br>
    <li class="list-group-item">3. set up git for cloud config (if its github set up a whole repository for it)</li>
    <br>
    <li class="list-group-item">4. cloud-config applications.properties file ->
        spring.application.name=spring-cloud-config-server
        server.port=8888
        spring.cloud.config.server.git.uri=https://github.com/nkr4m/microservice-playground
        spring.cloud.config.server.git.skip-ssl-validation=true
        management.security.enabled=false</li>
    <br>
    <li class="list-group-item">5. microservice which needs to use cloud config must have config client</li>
    <br>
    <li class="list-group-items">
        6. application.properties for the microservice to use cloud config ->
        spring.application.name=limits-service
        spring.config.import=configserver:http://localhost:8888
        #spring.application.name=limits-service
        spring.profiles.active=dev
        limits-service.min=2
        limits-service.max=998</li>
</ul>