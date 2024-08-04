pipeline{
agent any
stages{
stage('compile'){
steps{
bat 'javac Hey.java'
}
}
stage('run'){
steps{
bat 'java Hey.java'
}
}
}
  post {
        always {
            script {
                emailext (
                    to: 'ashwamedh.arote@gmail.com',
                    subject: "Build ${currentBuild.currentResult}: Job '${env.JOB_NAME}' (${env.BUILD_NUMBER})",
                    body: """
                    <p>Build ${currentBuild.currentResult}: Job '${env.JOB_NAME}' (${env.BUILD_NUMBER})</p>
                    <p>Build URL: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                    <p>Check the console output for details: <a href="${env.BUILD_URL}console">${env.BUILD_URL}console</a></p>
                    """,
                    attachLog: true // Attach the build log to the email
                )
            }
        }
    }
}
