pipeline {
    agent any
    stages{

        stage("Descargar código de la aplicación"){
            steps{
                git "https://github.com/cesarasanchezr/facturas-rest.git"
            } 
        }        

        stage("Creación de imagen"){
            steps{
                sh "docker build -t cesar.a.sanchez/facturas-node-16 ."
            } 
        }

       stage("Ejecución de contenedor"){
           steps {
               sh "docker run -d --name facturas-node -p 8081:8080 cesar.a.sanchez/facturas-node-16"
           }
           
        }

        stage("Test del servicio"){
            steps {
                echo "Probando el servicio ..."
            }
        }

        stage("Cerrar recursos"){
           steps {
                sh "docker stop facturas-node"
                sh "docker container rm facturas-node" 
            }            
        }
    }
}
