import org.csanchez.jenkins.plugins.kubernetes.pod.retention.PodRetention;

podTemplate(
    containers: [
        containerTemplate(
            name: 'gradle', 
            image: 'gradle:6.3-jdk14', 
            command: 'sleep', 
            args: '30d'
            podRetention: 'onFailure()'
        ),
    ],
) {
    node(POD_LABEL) {
        stage('Run pipeline against a gradle project') {
            container('gradle') {
                stage('Build a gradle project') {
                    git 'https://github.com/dlambrig/Continuous-Delivery-with-Docker-and-Jenkins-Second-Edition.git'
                    sh '''
                    cd Chapter08/sample1
                    chmod +x gradlew
                    ./gradlew test
                    '''
                }
            }
        }
    }
}

