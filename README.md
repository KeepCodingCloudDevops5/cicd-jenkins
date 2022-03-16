# cicd-jenkins

Materiales para la impartición del módulo "Ciclo de vida de un desarrollo: CI/CD" del bootcamp DevOps de KeepCoding.

Práctica 2 del módulo: Jenkins

## Requisitos
- docker (Aseguraté de que puedes correr `docker run hello-world` sin problemas)
- docker-compose (Aseguraté de que al correr `docker-compose --version` sale algo así como `docker-compose version 1.X.Y, build xxxxx`)
- Tener cuenta en docker hub https://hub.docker.com/
- Logarse en DockerHub vía consola de comandos con `docker login`

## Levantar master de jenkins
- Crea una carpeta llamada `jenkins_home` a la misma altura que el `docker-compose.yml`. La usaremos como volumen cuando corramos el contenedor de Jenkins.
- Corre `docker-compose up`. Deberías empezar a ver los logs de jenkins en la consola, entre ellos aparecerá la contraseña que tendrás que poner la primera vez, copialá.
- Abre http://localhost:8080 y usando la contraseña, crea un usuario. Enhorabuena, ya tienes tu instancia de Jenkins
- Plugins recomendados para la instalación: Folders, build timeout, timestamper, pipeline, pipeline: stage view, git, ssh build agents
- Posteriormente en "Manage jenkins" > "Plugins" podrás instalar otros interesantes, como Job DSL

## Desplegar un repositorio con Jenkins
1. Crea un repo público en github y añadelé cualquier de los Jenkinsfiles de la carpeta [Jenkinsfiles](./Jenkinsfiles/)
2. Usando el [Job DSL](https://jenkinsci.github.io/job-dsl-plugin/) crea un job en tu instancia de Jenkins para iterar tu proyecto. Tienes un ejemplo de la pinta que tendría el DSL [aquí](./DSL/)
3. Corre el seeder, se creará el pipeline de tu job
4. Corre el job, ejecutará los pasos que hayas especificado en tu Jenkinsfile en GitHub
5. Actualiza el Jenkinsfile en Github y vuelve a probar
