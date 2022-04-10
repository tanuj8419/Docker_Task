node {
   stage('Get Source') {
      // copy source code from local file system and test
      // for a Dockerfile to build the Docker image
      git ('https://github.com/tanuj8419/Docker_Task.git')
      if (!fileExists("Dockerfile")) {
         error('Dockerfile missing.')
      }
   }
   stage('Build Docker') {
       // build the docker image from the source code using the BUILD_ID parameter in image name
         sh "docker build -t flask ."
   }
   stage('Test image'){
        sh "docker run -d -p 80:5000 flask"
        sh 'echo "Container running"'
    }
   stage('Push image'){
        sh 'docker login -u "tanuj8419" -p "Tanuj@2303" docker.io'
        sh 'docker tag flask:latest tanuj8419/dockerhub:myimagepush'
        sh 'docker push tanuj8419/dockerhub:myimagepush'
   }

}