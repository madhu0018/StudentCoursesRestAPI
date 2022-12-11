pipeline {
    agent { label {label 'DOCKER'} }
    triggers { pollSCM('* * * * *') }
    stages{
        stage('git') {
            steps { git branch: 'master' ,
                   url :'https://github.com/madhu0018/StudentCoursesRestAPI.git'         
            }
        }
        stage ('buildDocker') {
            steps {
                  sh 'docker image build -t student:1.0 .'
                  sh 'docker image tag student:1.0 madhutony/student:1.0'
                  sh 'docker image push madhutony/student:1.0'
                  sh 'docker container run -d --name madhu -P madhutony/student:1.0'
                  sh 'docker container ls'   
            }

        }  
    }
} 