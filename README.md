# Github Action
You can write individual tasks called actions and combine them to create a customworkflow
# Events
push
pull request
issue (created, closed,..)
Events --> Workflow --> Job --> Step --> Action/CMD
Virtual Environment --> Runners --> Github hosted runner 
                                --> Self hosted runner

### Runner
1. any machine with the github action runner appilication installed
2. a runner is responsible for running you jovs wheneveran event happens and display back the result
3. it can be hosted by github or you can host your own runner

### Notification
Github profile --> Setting --> Notification --> System --> Actions

### Logs
1. download logs form 3 dots in right corner
2. To get debug mode
setting --> secret --> New Secret
```
Name ACTIONS_RUNNER_DEBUG
secret true
```