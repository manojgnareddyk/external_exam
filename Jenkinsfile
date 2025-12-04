pipeline{
    agent any{
        stages{
            stage("Build"){
                steps{
                    echo "Building"
                    bat "docker build -t kubedemoapp ."
                }
            }
            stage('Docker login'){
                steps{
                    echo "Docker Login"
                    bat "docker login"
                }
            }
            stage('Docker Push'){
                steps{
                    echo "Push the image to Docker Hub"
                    bat "docker tag kubedemoapp:v1 manojgnareddyk/exam:v1"
                    bat "docker push manojgnareddyk/exam:v1"
                }
            }
            stage("Deplay to kubernetes"){
                steps{
                    echo " Deploy to kubernetes"
                    bat "kubectl apply -f deployment.yaml --validate=false"
                    bat "kubectl apply -f service.yaml"
                }
            }
        }
    }
        post{
            succes{
                echo "Pipeline built successfully"
            }
            failure{
                echo "Pipeline failed"
            }
        }
    

}



