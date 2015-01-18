---
layout: page
title: "Configuration"
category: ref
weight: 2
date: 2014-12-29 23:49:54
---
To be able to run JMoribus stories you'll have to configure the application.

## Default configuration
This can be done by creating the `DefaultConfiguration` and adding your own steps and reporters.
See the next example:

```java
Configuration config = new DefaultConfiguration();
config.addSteps(listOfObjectsHoldingSteps);
config.addReporter(theDefaultOrOwnImplementationOfTheReporter);
JMoribus jMoribus = new JMoribus(configuration);
jMoribus.runStories(listOfStories);
```

## Running stories
The stories need to be parsed and passed down to JMoribus.

### Parsing the stories
JMoribus comes with a parser of its own to generate objects from story files.
You'll have to provide the parser with an `InputStream` holding the story.
This you'll have to add this in an `ParseableStory` with a title.
See the next example:

```java
List<ParseableStory> parseableStories = new ArrayList<>(3);
InputStream fileInputStream = getClass().getResourceAsStream("/multiScenario.story");
parseableStories.add(new ParseableStory(fileInputStream, "MultiScenarioTitle"));
fileInputStream = getClass().getResourceAsStream("/test2.story");
parseableStories.add(new ParseableStory(fileInputStream, "testTitle"));
fileInputStream = getClass().getResourceAsStream("/referring.story");
parseableStories.add(new ParseableStory(fileInputStream, "PrologueTest"));

List<Story> stories = StoryParser.parseStories(parseableStories);
```

When an story is not parseable the parser will throw an `UnableToParseStoryException`.

### Running it
When the parser has parsed the stories you can feed them to JMoribus just like it was explained in the default configuration.