# Terminal

To list any process listening to the port 8080:

`lsof -i:8080`

To kill any process listening to the port 8080:

`kill $(lsof -t -i:8080)`

or more violently:

`kill -9 $(lsof -t -i:8080)`

(-9 corresponds to the SIGKILL - terminate immediately/hard kill signal: see List of Kill Signals and What is the purpose of the -9 option in the kill command?. If no signal is specified to kill, the TERM signal a.k.a. -15 or soft kill is sent, which sometimes isn't enough to kill a process.).

