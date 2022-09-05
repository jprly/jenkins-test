def win32BuildBadge = addEmbeddableBadgeConfiguration(id: "win32build", subject: "Windows Build")

def RunBuild() {
    echo 'Sleeping instead of running the build'
    sleep 10
}

pipeline {
    agent any
    stages {
        stage('Building') {
            steps {
                script {
                    win32BuildBadge.setStatus('running')
                    try {
                        RunBuild()
                        win32BuildBadge.setStatus('passing')
                    } catch (Exception err) {
                        win32BuildBadge.setStatus('failing')

                        /* Note: If you do not set the color
                                 the configuration uses the best status-matching color.
                                 passing -> brightgreen
                                 failing -> red
                                 ...
                        */
                        win32BuildBadge.setColor('pink')
                        error 'Build failed'
                    }
                }
            }
        }
    }
}
