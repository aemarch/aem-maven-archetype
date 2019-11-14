# aem-maven-archetype
<<< How to generate an Adobe Experience Manager Archetype project locally.>>
Since Maven Archetype Plugin 3.0.0 the archetype resolution has changed which may leave you with errors when attempting to generate a new Maven Adobe Archetype project using previous commands and settings.xml outlined in existing Adobe documentation.

Errors like:

[WARNING] Archetype not found in any catalog. Falling back to central repository.
[WARNING] Add a repository with id 'archetype' in your settings.xml if archetype's repository is elsewhere.
[WARNING] The POM for com.adobe.granite.archetypes:aem-project-archetype:jar:23 is missing, no dependency information available
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  3.877 s
[INFO] Finished at: 2019-11-14T13:20:36-05:00
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-archetype-plugin:3.1.2:generate (default-cli) on project standalone-pom: The desired archetype does not exist (com.adobe.granite.archetypes:aem-project-archetype:18) -> [Help 1]
[ERROR]


If you're reciving a similar error do the following:

1) Download the aem-project-archetype-23-SNAPSHOT.jar from this project.
2) Update the -DarchetypeRepository value in the command below to the location of the downloaded jar. 
3) Create the root project folder and run 

mvn archetype:generate \
  -DarchetypeGroupId=com.adobe.granite.archetypes \
  -DarchetypeArtifactId=aem-project-archetype \
  -DarchetypeRepository=~/Downloads/'aem-project-archetype-23-SNAPSHOT.jar'
  
This will circumvent the search for the archetype from the repository and use the local archetype instead.
