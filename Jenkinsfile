node {
  def myGradleContainer = docker.image('gradle:jdk8')
  myGradleContainer.pull()
  stage('prep') {
    checkout scm
  }
  stage('test') {
     //${env.HOME}/.gradle
     myGradleContainer.inside("-v /mnt/a/data01/jenkins_home/.gradle:/home/gradle/.gradle") {
       sh 'cd complete && gradle test'
     }
  }
  stage('run') {
    // ${env.HOME}/.gradle
     myGradleContainer.inside("-v /mnt/a/data01/jenkins_home/.gradle:/home/gradle/.gradle") {
       sh 'cd complete && gradle run'
     }
  }
}
