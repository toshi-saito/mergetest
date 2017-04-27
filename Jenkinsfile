node {
  checkout scm 
  stage("docker build") {
    docker.build("usagi")
  }

  stage("in docker") {  
    docker.image("usagi").inside("-u 0:0") {

      stage("Boot services") {
        sh '/etc/init.d/mariadb restart'
        sh '/etc/init.d/postgresql restart'
      }

      stage("checkout") {
        checkout scm;
      }
    }
  }
}

