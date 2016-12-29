node ('master') {
    parallel first:{
                stage 'Stage 1'
                echo 'Stage 1'
                },
            second:{
                stage 'Stage 2'
                echo 'Stage 2'
                writeFile file:'testfile.txt', text:'is this going to append?'
                def fileContent = readFile file:'testfile.txt'
                 echo "$fileContent"
                 //archive '*.txt'
                // step([$class: 'ArtifactArchiver', artifacts: '**/*.txt', fingerprint: true])
                step([$class: 'ArtifactArchiver', artifacts: '*.txt', excludes: null, fingerprint: true, onlyIfSuccessful: true])
               stash name:"testfile-stash" , includes:'**/*.txt'
            }
            
            stage 'Stage 3'
            echo 'I am on feature-1 branch now'
            
            unstash "testfile-stash"
            def fileContent1 = readFile file:'testfile.txt'
                 echo "$fileContent1"
    input message: 'Approve?'
    
}
