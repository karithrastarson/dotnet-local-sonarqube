# Running Sonar locally


## Prerequisite
Install SonarScanner globally:

`dotnet tool install --global dotnet-sonarscanner`

## Setup your project in Sonar
1. Run `sudo sysctl -w vm.max_map_count=262144` to increase max memory for virtual machines. 
2. Run `docker-compose up`
3. Navigate to http://localhost:9000/ 
4. Choose Add Project and give it a project key. Example: test-project
5. Generate a token and note it down. Example: `dcf2578f94df1c49d2fcc3a61ac054a0d5cdf9ec`

## Run an analysis
1. Navigate to the root of the project.
2. Run `dotnet sonarscanner begin /k:test-project /d:sonar.host.url=http://localhost:9000 /d:sonar.login=dcf2578f94df1c49d2fcc3a61ac054a0d5cdf9ec /o:test-project`
3. Run `dotnet build`
4. Run `dotnet sonarscanner end /d:sonar.login=dcf2578f94df1c49d2fcc3a61ac054a0d5cdf9ec`