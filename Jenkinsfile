node('nodejs') {
    stage('Checkout') {
git url: 'https://github.com/imejri/DO400-apps', branch: 'scripted-pipelines'
    }

    stage('Test') {
        if (isChanged('simple-webapp/backend')) {
            echo 'Detected Backend changes'
            sh 'node ./simple-webapp/backend/test.js'
        } // if

        if (isChanged('simple-webapp/frontend')) {
            echo 'Detected Frontend changes'
            sh 'node ./simple-webapp/frontend/test.js'
        } // if
    } // stage
}
    def isChanged(dir) {
    changedFilepaths = sh(
        script: 'git diff-tree --no-commit-id --name-only -r HEAD',returnStdout: true).trim().split('\n')
        for (filepath in changedFilepaths) {
            if (filepath.startsWith(dir)) {
            return true;
            }
        } // for
        return false
    // fin def
    
} // node