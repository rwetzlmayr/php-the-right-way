---
isChild: true
title: Verhaltensgetriebe Entwicklung
---

## Verhaltensgetriebe Entwicklung {#behavior_driven_development_title}

Es gibt zwei Arten verhaltensgetriebener Entwicklung (Behavior-Driven Development, BDD): SpecBDD und StoryBDD. SpecBDD konzentriert sich auf das technische Verhalten oder Code, während sich StoryBDD auf Geschäfts- oder Eigenschaftenverhalten oder Interaktionen fokussiert. Es gibt Framework für beiden Typen in PHP.

Für StoryBDD schreibt man menschenlesbare Geschichten, die das Verhalten deiner Anwendung beschreiben. Diese Geschichten können als tatsächliche Tests für deine Anwendung geprüft werden. Als Framework für StoryBDD in PHP wird Behat verwendet, das von Rubys [Cucumber](http://cukes.info/) inspiriert wurde und das Gherkin als DSL zur Beschreibung des Eigenschaftsverhaltens implementiert.

Für SpecBDD schreibst du Spezifikationen, die beschreiben, wie sich dein tatsächlicher Code verhalten soll. Statt eine Funktion oder Methode zu testen wird beschrieben, wie sich diese Funktion oder Methode verhalten soll. PHP bietet für diesen Zweck das Framework PHPSpec, das von [RSpec project](http://rspec.info/) für Ruby inspiriert wurde.


### BDD-Links

* [Behat](http://behat.org/), das Framework für StoryBDD in PHP, inspiriert von Rubys [Cucumber](http://cukes.info/)-Projekt;
* [PHPSpec](http://www.phpspec.net/), das Framework für SpecBDD in PHP, inspiriert von Rubys [RSpec](http://rspec.info/)-Projekt;
* [Codeception](http://www.codeception.com) ist ein vollständiges Testframework, das BDD verwendet.
