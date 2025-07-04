pipeline {
    agent any

    environment{
        DOCKER_IMAGE = 'apimonedastt'
        CONTAINER_NAME = 'docker'
        DOCKER_NETWORK = 'dockermonedas_red'
        DOCKER_BUILD_DIR = 'presentacion'
        HOST_PORT = '9090'
        CONTAINER_PORT = '8080'
    }

    stage {
        stage ('compilacion maven') {
            steps{
                bat 'mvn clean package - Dskiptests'

            }
        }        
        stage ('construir imagen'){
            steps{
                dir("${DOCKER_BUILD_DIR}") {
                    bat "dokcer build . -t ${DOCKER_IMAGE}"
                }
            }
        }
        stage ('Desplegar contenedor'){
            steps {
                
                    bat "docker run --network ${DOCKER_NETWORK} --name ${CONTAINER_NAME} -p ${OST_PORT}:${TAINER_PORT} -d ${DOCKER_IMAGE}"
                

            }
        }
    }

}