#!groovy

node('master') {

    stage('Clean Workspace') {
        deleteDir()
    }

    stage('Checkout Tools-Belt') {
	     checkout scm
    }

    stage('deploy') {

      withCredentials([usernamePassword(credentialsId: 'docker-admin', usernameVariable: 'dockerUser', passwordVariable: 'dockerPassword')]) {
          sh 'ansible-playbook -i hosts docker_playbook.yml --extra-vars "docker_user_name=${dockerUser} docker_password=${dockerPassword}"'
      }
    }
}
