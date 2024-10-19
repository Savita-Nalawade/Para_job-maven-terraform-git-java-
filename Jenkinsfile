pipeline {
    agent any
    parameters {
        string(name: 'maven_version', defaultValue: '3.9.3', description: 'Pass the version of Maven')
        string(name: 'terraform_version', defaultValue: '1.8.5', description: 'Pass the version of Terraform')    
        string(name: 'git_version', defaultValue: '2.46.1', description: 'Pass the version of Git')
        string(name: 'java_version', defaultValue: '17', description: 'Pass the major version of Java (e.g., 17)')
        string(name: 'java_patch_version', defaultValue: '0.12', description: 'Pass the patch version of Java (e.g., 0.12)')
    }
    stages {
        stage('Download Maven') {
            steps {
                sh '''
                cd /var/lib/jenkins/
                sudo wget https://dlcdn.apache.org/maven/maven-3/${maven_version}/binaries/apache-maven-${maven_version}-bin.tar.gz
                sudo tar -xzf apache-maven-${maven_version}-bin.tar.gz
                sudo rm apache-maven-${maven_version}-bin.tar.gz
                '''
            }
        }
        stage('Download Terraform') {
            steps {
                sh '''
                cd /opt
                sudo wget https://releases.hashicorp.com/terraform/${terraform_version}/terraform_${terraform_version}_linux_amd64.zip
                sudo unzip terraform_${terraform_version}_linux_amd64.zip
                sudo rm terraform_${terraform_version}_linux_amd64.zip
                '''
            }
        }    
        stage('Download Git') {
            steps {
                sh '''
                cd /var/lib/jenkins/
                sudo wget https://github.com/git/git/archive/refs/tags/v${git_version}.tar.gz
                sudo tar -xzf v${git_version}.tar.gz
                sudo rm v${git_version}.tar.gz
                '''
            }
        }
        stage('Download Java') {
            steps {
                sh '''
                cd /opt
                sudo wget https://download.oracle.com/java/${java_version}/archive/jdk-${java_version}.${java_patch_version}_linux-x64_bin.tar.gz
                sudo tar -xzf jdk-${java_version}.${java_patch_version}_linux-x64_bin.tar.gz
                sudo rm jdk-${java_version}.${java_patch_version}_linux-x64_bin.tar.gz
                '''
            }
        }    
    }
}
