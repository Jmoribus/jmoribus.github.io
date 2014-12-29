---
layout: page
title: "Annotations"
category: ref
weight: 2
date: 2014-12-29 22:49:33
---
#### Step annotations
To get the stories working with the java code, we can use the Jmoribus Annotations `@Given`,`@When` and `@Then`.
For example:

```Java
@Given("a system $state")
public void aSystemState(String state) {
    System.setState(state);
}

@When("I do something")
public void doSomething() {
    System.doSomeThing();
}

@Then("system is in a different $state")
public void checkState(String state) {
    Assert.assertEquals(state,System.getState());
}
```

In order to create aliases for the step you can use the same annotation, like so:

```Java
@Given({"a system $state",
        "a other system $state"})
public void aSystemState(String state) {
    System.setState(state);
}
```

#### Before/After annotations
Jmoribus know a few before and after hooks.
This can be used before or after a story or scenario.

```Java
    @BeforeStory
    @BeforeScenario
    @AfterScenario
    @AfterStory
    public void beforeOrAfter() {
        // Do something
    }
```

#### Documentation/API annotations
Jmoribus can store variables so it can actively check if the needed variables do exist.
Jmoribus knows the following annotations for this feature:

```Java
    @RequiredVariables("requiredVariableA")
    @Given("a step that requires a variable")
    public void methodA() {
        // do something with requiredVariableA here
    }
    @OutputVariables("outputVariableA")
    @When("a step that creates a variable")
    public void methodB() {
        // set the output variable here
    }
```

Jmoribus will check the ContextProvider thats given to the [Configuration]({% post_url 2014-12-29-configuration %}).