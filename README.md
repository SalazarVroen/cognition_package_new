# Cognition Package

[![pub package](https://img.shields.io/pub/v/cognition_package.svg)](https://pub.dartlang.org/packages/cognition_package)
[![style: recommended](https://img.shields.io/badge/style-lint-4BC0F5.svg)](https://pub.dev/packages/lints)
[![github stars](https://img.shields.io/github/stars/cph-cachet/cognition_package.svg?style=flat&logo=github&colorB=deeppink&label=stars)](https://github.com/cph-cachet/cognition_package)
[![MIT License](https://img.shields.io/badge/license-MIT-purple.svg)](https://opensource.org/licenses/MIT)

[Cognition Package](https://carp.cachet.dk/cognition-package/) is a Flutter [package](https://pub.dartlang.org/packages/cognition_package) for building cognitive tests for study apps on Android and iOS built using the [Research Package](https://pub.dartlang.org/packages/research_package).

The overarching goal of Cognition Package is to enable developers and researchers to design and build cross-platform (iOS and Android) cognitive assessment applications that rely on validated gold-standard cognitive tests.
When combined with [Research Package](https://pub.dartlang.org/packages/research_package), Cognition Package meets the requirements of most scientific research, including capturing participant consent, extensible input tasks, and the security and privacy needs necessary for IRB approval.

Cognition Package is a Flutter implementation of a cognitive test battery including 14 validated gold-standard cognitive tests spanning all 8 neurocognitive domains:

1. Sensation
2. Perception
3. Motor skills and construction
4. Attention and concentration
5. Memory
6. Executive functioning
7. Processing speed
8. Language and verbal skills

Each test in Cognition Package is implemented as an [`RPActivityStep`](https://pub.dev/documentation/research_package/latest/research_package_model/RPActivityStep-class.html) from [Research Package](https://pub.dartlang.org/packages/research_package).
As such, they may be used inside an [`RPTask`](https://pub.dev/documentation/research_package/latest/research_package_model/RPTask-class.html) along with other types of [`RPStep`](https://pub.dev/documentation/research_package/latest/research_package_model/RPStep-class.html)s.

Each test consists of 3 key sections; the instructions for the test, the test itself, and the test results. Hence, each test includes 3 classes that defines:

1. The model class which extends `RPActivityStep` and defines the parameters available for the specific test (e.g., the length of the test or the amount of repetitions), as well as the function to calculate the final score of the test.
2. The UI class which describes how the test is rendered on the screen and the logic of running the test.
3. The [`RPResult`](https://pub.dev/documentation/research_package/latest/research_package_model/RPResult-class.html) class which describes the data collected from the test and adds it to the list of all results from the task.

The current set of cognitive tests in the Cognition Package are:

1. [Multiple Object Tracking](https://en.wikipedia.org/wiki/Multiple_object_tracking)
2. [Corsi Block Tapping](https://en.wikipedia.org/wiki/Corsi_block-tapping_test)
3. [Verbal Recognition Memory](https://link.springer.com/referenceworkentry/10.1007/978-0-387-79948-3_1162)
4. [Delayed Recall](https://www.psychdb.com/cognitive-testing/moca#delayed-recall)
5. [Flanker](https://en.wikipedia.org/wiki/Eriksen_flanker_task)
6. [Letter Tapping](https://www.psychdb.com/cognitive-testing/moca#attention-vigilance)
7. [Paired Associative Learning](https://www.cambridgecognition.com/cantab/cognitive-tests/memory/paired-associates-learning-pal/)
8. [Picture Sequence Memory](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4254833/)
9. [Rapid Visual Information Processing](https://www.cambridgecognition.com/cantab/cognitive-tests/attention/rapid-visual-information-processing-rvp/)
10. [Reaction Time](https://www.psytoolkit.org/lessons/simple_choice_rts.html)
11. [Stroop Effect](https://en.wikipedia.org/wiki/Stroop_effect)
12. [Finger Tapping](https://link.springer.com/referenceworkentry/10.1007/978-1-4419-1698-3_343)
13. [Trail Making](https://en.wikipedia.org/wiki/Trail_Making_Test)
14. [Visual Array Change](https://jov.arvojournals.org/article.aspx?articleid=2422328)

Cognition Package is part of the overall [Copenhagen Research Platform (CARP)](https://carp.cachet.dk) which also provides a Flutter package for mobile and wearable sensing called [CARP Mobile Sensing](https://pub.dev/packages/carp_mobile_sensing).

## Documentation

There is a set of tutorials, describing:

- the overall [software architecture](https://carp.cachet.dk/research-package/) of Research Package
- the overall [software architecture](https://carp.cachet.dk/cognition-package/) of Cognition Package
- how to create a [cognitive test](https://carp.cachet.dk/creating-cognitive-tests/)
- the [cognition_package Flutter API](https://pub.dev/documentation/cognition_package/latest/) is available (and maintained) as part of the package release at pub.dev
- [localization](https://carp.cachet.dk/localization/) support in Research Package which also applies for Cognition Package

## Example Application

There is an [example app](https://github.com/cph-cachet/cognition_package/tree/main/example) which demonstrates the different features of Cognition Package as implemented in a Flutter app.

The cognitive test to be shown in the example app can be configured in the `cognition_config.dart` file:

```dart
// Here the list of cognitive test are added to an RP ordered task.
// Uncomment the ones you want to see a demo of.
RPOrderedTask cognitionTask = RPOrderedTask(
  identifier: 'cognition_demo_task',
  steps: [
    reactionTime,
    pairedAssociatesLearning,
    tapping,
    corsiBlockTapping,
    stroopEffect,
    rapidVisualInfoProcessing,
    trailMaking,
    continuousVisualTracking,
    wordRecall,
    pictureSequenceMemory,
    letterTapping,
    flanker,
    visualArrayChange,
    delayedRecall,
    completionStep,
  ],
);
```

The `cognitionTask` defines the list of cognitive tasks to be shown and you may include the ones you want to see.

## Localization

Cognition Package support localization via the [localization support in Research Package](https://carp.cachet.dk/localization/). Currently, the package supports English (`en`), Danish (`da`), French (`fr`), and Portuguese (`pt`).

> **Note:** The sounds used in the Letter Tapping test and Word Recall tests for now only use English letters and words. This might be translated in a future version of the package and PRs for this is most welcome.

In order to support localization in your app, add the `RPLocalizations.delegate` and the `CPLocalizations.delegate` delegates to your list of delegates in your `MaterialApp` configuration. See the [`main.dart`](https://github.com/cph-cachet/cognition_package/blob/main/example/lib/main.dart) in the example app for how this can be done.

## Who is backing this project?

Cognition Package is made by the [Copenhagen Center for Health Technology (CACHET)](https://www.cachet.dk/) and is a component in the [Copenhagen Research Platform (CARP)](https://carp.cachet.dk), which is used in a number of applications and studies.

## How can I contribute?

We are more than happy to take contributions and feedback.
Use the [Issues](https://github.com/cph-cachet/cognition_package/issues) page to file an issue or feature request.
Besides general help for enhancement and quality assurance (bug fixing), we welcome input on new cognitive tests.

## Copyright

Note that the tests in this package may be **subject to different copyright terms**.
It is your responsibility to investigate if you can use these tests for your specific purpose and application, and if you need to obtain a permission from the copyright holder(s).

In the table below, we have provided links to copyright statements (where applicable), which you may want to consult, if you're using a test. If it states **(c) CACHET** this implies that the test is designed by us, and hence copyright (MIT license) to CACHET.

> Note, however, as per the [MIT license](https://github.com/cph-cachet/cognition_package/blob/master/LICENSE), _this software is provided "as is" and in no event shall the authors (i.e., us) be liable for any claim - including copyright issues - arising from the use of this software_.

| **Test**                            | **Copyright**                                                                                                                                              |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Multiple Object Tracking            | (c) CACHET                                                                                                                                                 |
| Corsi Block Tapping                 | [PsyToolkit](https://www.psytoolkit.org/copyright.html)                                                                                                    |
| Verbal Recognition Memory           | [MoCa](https://www.mocatest.org/permission/)                                                                                                               |
| Delayed Recall                      | [MoCa](https://www.mocatest.org/permission/)                                                                                                               |
| Flanker                             | (c) CACHET                                                                                                                                                 |
| Letter Tapping                      | [MoCa](https://www.mocatest.org/permission/)                                                                                                               |
| Paired Associative Learning         | [Cambridge Cognition Ltd](https://www.cambridgecognition.com/company/terms-of-use)                                                                         |
| Picture Sequence Memory             | [NIHTB-CB](https://www.healthmeasures.net/images/nihtoolbox/NIH_Toolbox_Emotion_zip_file/Terms_of_Use_HM_approved_1-12-17_-_Updated_Copyright_Notices.pdf) |
| Rapid Visual Information Processing | [Cambridge Cognition Ltd](https://www.cambridgecognition.com/company/terms-of-use)                                                                         |
| Reaction Time                       | (c) CACHET                                                                                                                                                 |
| Stroop Effect                       | (c) CACHET                                                                                                                                                 |
| Finger Tapping                      | (c) CACHET                                                                                                                                                 |
| Trail Making                        | [public domain](https://datashare.nida.nih.gov/instrument/trail-making-test)                                                                               |
| Visual Array Change                 | (c) CACHET                                                                                                                                                 |

## License

This software is copyright (c) [Copenhagen Center for Health Technology (CACHET)](https://www.cachet.dk/) at the [Technical University of Denmark (DTU)](https://www.dtu.dk).
This software is available 'as-is' under a [MIT license](https://github.com/cph-cachet/cognition_package/blob/main/LICENSE).
