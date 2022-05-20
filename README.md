# example-maven-deploy

### build and deploy
```sh
mvn clean package
mvn deploy
```

## important files

#### pom.xml 
- should have `<distributionManagement>`

#### settings.xml
- `<servers><server><id>` block with id should be matching with `<distributionManagement><repository><id>` where we want to deploy
- The Maven install: `${maven.home}/conf/settings.xml`
- A user's install: `${user.home}/.m2/settings.xml`

### Note:
- Repo type should be hosted else it will give 405 error
- If you upload the same build it will give 400 error
- Need to update `<version>` in pom.xml if you need to publish with same name 

#### docker run sonatype/nexus3
```sh
docker run -d -p 8081:8081 --name nexus sonatype/nexus3
```

## Refrences:
- https://stackoverflow.com/questions/18649486/error-when-deploying-an-artifact-in-nexus
- https://stackoverflow.com/questions/24122382/how-to-configure-maven2-to-publish-to-artifactory
- https://www.devopsschool.com/tutorial/artifactory/upload-artifacts-using-maven-in-artiactory.html
- https://maven.apache.org/settings.html
- https://spring.io/guides/gs/maven/