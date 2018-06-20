# Java app setup for Rubyists


## Audience

This guide is intended for non-Java developers setting up Java apps for the first time. I assume basic profiency with the command line. I will compare some aspects of the Java environment with common counterparts in the Ruby ecosystem.


## Quick Start

1. Complete all steps in [Platform Tools Installation][pti-sharepoint].
2. Copy the [Ramsey standard Maven settings][maven-settings] to `~/.m2/settings.xml`.
3. Clone the repository of at least one Java app currently in development, e.g. I am starting with [Money Spoke Bundle API][MSB-API], which will almost certainly _not_ see continued active development.
4. Setup any project-specific environment variables (these should be documented in the project’s readme), preferably using `direnv`’s `.envrc`. If any environment variables have separate settings for integration tests, be sure to use those settings, at least for now.
5. Install the project dependencies (and run the test suite): `mvn install`.


## IntelliJ IDEA

This IDE is both deep and wide, and won't always hold your hand. You've already seen some of this from the [Platform Tools Installation][pti-sharepoint], and below are some other scenarios you are likely to encounter. I am using version _IntelliJ IDEA 2018.1.5 (Community Edition)_ and some of these instructions will probably be inaccurate for some future versions of the product.

### Project setup

1. Launch IntelliJ IDEA
2. Open the project
3. Select “Run” > “Edit Configurations…”
4. Click the “+” and select “Cucumber Java”
    1. Set the name (e.g. “Cucumber”)
    1. Click the “…” button to the right of the “Main class” field and select “Main” from the list
    2. Set “Feature or folder path” to src/test
    3. Click the “…” button to the right of “Environment variables”
        1. Use the “+” button to set up all of the project-specific ENVs you set in `.envrc` earlier
        2. Click “OK”
    4. Click on the “Use classpath of module” dropdown and select the current project
    5. Click “OK”
  5. Select “Run” > “Run…”
  6. 

### “Project SDK is not defined”

This banner shows up at the top of the main editor. To resolve this:

1. click on “Setup SDK” on the right side of the banner - if this is a new installation, the modal box will say “Nothing to show”;
2. click “Configure…” - again this will have “Nothing to show” on a new installation;
3. click the “+” at the top of the left-hand list;
4. click “JDK” - after a pause, this will bring up a file selection dialog box which _should_ already be set to `$JAVA_HOME`, which for me currently is `/Library/Java/JavaVirtualMachines/jdk1.8.0_172.jdk/Contents/Home`;
5. click “Open” - this will add “1.8” to the left-hand list and show a number of files;
6. click “OK” in the bottom-right corner of the “Configure SDK” window; and
7. click “OK” in the “Select Project SDK” window.


## Maven

Maven brings convention-over-configuration to many parts of Java development; in terms of daily dev usage, it is similar to a combination of bundler and Rake. For a decent introduction to Maven, try the free [Maven by Example][maven-by-example] ebook.


[maven-by-example]: https://www.sonatype.com/ebooks
[maven-settings]: https://github.com/lampo/dev-standards/blob/master/java/maven/settings.xml
[MSB-API]: https://github.com/lampo/money-spoke-bundle-api
[pti-sharepoint]: https://lampogroup.sharepoint.com/tech/DigitalProductManagement/EveryDollarDigitalManagement/SitePages/Engineering/Platform%20Tools%20Installation.aspx
