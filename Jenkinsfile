node("docker") {
    docker.withRegistry('axamon/testci', 'alberto.bregliano@gmail.com') {
    
        git url: "https://github.com/axamon/testci.git", credentialsId: 'axamon'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "your-project-name"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
