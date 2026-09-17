Install sonarqube plugin

add below to pom.xml
<plugin>
                <groupId>org.sonarsource.scanner.maven</groupId>
                <artifactId>sonar-maven-plugin</artifactId>
                <version>3.11.0.3922</version>
            </plugin>



kubectl create secret docker-registry acr-secret \
	--docker-server=democontainerregi.azurecr.io \
	--docker-username=democontainerregi \
	--docker-password=7OlnhEm5MMMC7SngZmtFXHCeFSvHODLFluzrIxukxwKq3n9qWvjnJQQJ99CIACGhslBEqg7NAAACAZCRZpNT