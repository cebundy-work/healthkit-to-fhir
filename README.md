+⚠️ **Repository Archived – MedTech OSS**

`Status: Archived as of April 13, 2026`


This repository is part of the open-source assets associated with the Microsoft MedTech service. The MedTech service has been formally deprecated, and there are no remaining active customers using the service. As a result, this repository is no longer maintained and has been archived to prevent confusion for customers and the broader open-source community.

As of **April 13, 2026**, this open-source repository has been archived and will not receive updates, bug fixes, or security patches. Microsoft recommends that customers evaluate currently supported Azure Health Data Services capabilities for device data interoperability and transformation scenarios.



**Why this repository is being archived**

Following the deprecation of the MedTech service and the completion of customer transitions away from the platform, Microsoft has made the decision to discontinue ongoing maintenance of associated open-source repositories. Continuing to host these projects as active may create the impression of ongoing support or recommended usage, which is no longer accurate.


**Important dates**

- May 3, 2025 – Initiation of MedTech service deprecation and prevention of new instance creation
- April 13, 2026 – Archival of this open-source repository

**Acknowledgements**

We would like to sincerely thank the community of contributors, collaborators, and customers who engaged with this project over time. Your feedback, issue reports, documentation improvements, and code contributions helped shape the evolution of device data interoperability solutions within Microsoft’s healthcare ecosystem.

**What’s next?**

Microsoft continues to invest in healthcare interoperability, cloud-native data platforms, and AI-powered transformation services across Azure Health Data Services and related offerings. Future innovation in this space is being delivered through actively supported Microsoft healthcare platform capabilities.
To learn more about current Microsoft healthcare interoperability solutions, please refer to:

- [ Azure Health Data Services](https://learn.microsoft.com/en-us/azure/healthcare-apis/)
- [FHIR service in Azure Health Data Services](https://learn.microsoft.com/en-us/azure/healthcare-apis/fhir/)
- Community discussions on https://stackoverflow.com/questions/tagged/azure-health-data-services

**Archived content disclaimer**

The content in this repository is no longer actively maintained and may be out of date or no longer accurate. Dependencies, APIs, deployment models, or referenced services may have changed since the time of last update.

⚠️ **Security Notice:**

Archived repositories do not receive security updates, bug fixes, or compatibility improvements. Use of this code in production environments may introduce security or operational risks. Microsoft recommends against deploying or relying on archived repositories in active workloads.

**The original README content has been preserved below for historical reference.**+⚠️ **Repository Archived – MedTech OSS**

`Status: Archived as of April 13, 2026`


This repository is part of the open-source assets associated with the Microsoft MedTech service. The MedTech service has been formally deprecated, and there are no remaining active customers using the service. As a result, this repository is no longer maintained and has been archived to prevent confusion for customers and the broader open-source community.

As of **April 13, 2026**, this open-source repository has been archived and will not receive updates, bug fixes, or security patches. Microsoft recommends that customers evaluate currently supported Azure Health Data Services capabilities for device data interoperability and transformation scenarios.



**Why this repository is being archived**

Following the deprecation of the MedTech service and the completion of customer transitions away from the platform, Microsoft has made the decision to discontinue ongoing maintenance of associated open-source repositories. Continuing to host these projects as active may create the impression of ongoing support or recommended usage, which is no longer accurate.


**Important dates**

- May 3, 2025 – Initiation of MedTech service deprecation and prevention of new instance creation
- April 13, 2026 – Archival of this open-source repository

**Acknowledgements**

We would like to sincerely thank the community of contributors, collaborators, and customers who engaged with this project over time. Your feedback, issue reports, documentation improvements, and code contributions helped shape the evolution of device data interoperability solutions within Microsoft’s healthcare ecosystem.

**What’s next?**

Microsoft continues to invest in healthcare interoperability, cloud-native data platforms, and AI-powered transformation services across Azure Health Data Services and related offerings. Future innovation in this space is being delivered through actively supported Microsoft healthcare platform capabilities.
To learn more about current Microsoft healthcare interoperability solutions, please refer to:

- [ Azure Health Data Services](https://learn.microsoft.com/en-us/azure/healthcare-apis/)
- [FHIR service in Azure Health Data Services](https://learn.microsoft.com/en-us/azure/healthcare-apis/fhir/)
- Community discussions on https://stackoverflow.com/questions/tagged/azure-health-data-services

**Archived content disclaimer**

The content in this repository is no longer actively maintained and may be out of date or no longer accurate. Dependencies, APIs, deployment models, or referenced services may have changed since the time of last update.

⚠️ **Security Notice:**

Archived repositories do not receive security updates, bug fixes, or compatibility improvements. Use of this code in production environments may introduce security or operational risks. Microsoft recommends against deploying or relying on archived repositories in active workloads.

**The original README content has been preserved below for historical reference.**
# HealthKitToFhir Swift Library

[![Build Status](https://microsofthealth.visualstudio.com/Health/_apis/build/status/POET/HealthKitToFhir_Daily?branchName=master)](https://microsofthealth.visualstudio.com/Health/_build/latest?definitionId=435&branchName=master)

The HealthKitToFhir Swift Library provides a simple way to create FHIR® Resources from HKObjects.

## Installation

HealthKitToFhir uses **Swift Package Manager** to manage dependencies. It is recommended that you use Xcode 11 or newer to add HealthKitToFhir to your project.

1. Using Xcode 11 go to File > Swift Packages > Add Package Dependency
2. Paste the project URL: https://github.com/microsoft/healthkit-to-fhir
3. Click on next and select the project target

## Basic Usage

### Create the factory

Resources are created using "Factory" classes that can be initialized with an optional JSON configuration to provide additional conversion data used to decorate the Resource. In the example below, an observation factory is initialized with no configuration.

```swift
do {
    let  factory = try ObservationFactory()
} catch {
    // Handle errors
}
```

### Use the factory for creating resources

```swift
do {
    let observation = try factory.observation(from: healthKitObject)
} catch {
    // Handle errors
}
```

## Supported conversions

### Observations

Additional observation conversions can be added by providing a custom configuration to the ObservationFactory when it is initialized at runtime.

- HKQuantityTypeIdentifierHeartRate
- HKCorrelationTypeIdentifierBloodPressure
- HKQuantityTypeIdentifierBloodPressureDiastolic
- HKQuantityTypeIdentifierBloodPressureSystolic
- HKQuantityTypeIdentifierStepCount
- HKQuantityTypeIdentifierBloodGlucose
- HKQuantityTypeIdentifierOxygenSaturation
- HKQuantityTypeIdentifierBodyMass
- HKQuantityTypeIdentifierBodyTemperature
- HKQuantityTypeIdentifierRespiratoryRate
- HKQuantityTypeIdentifierHeight
- HKQuantityTypeIdentifierRestingHeartRate
- HKQuantityTypeIdentifierHeartRateVariabilitySDNN
- HKQuantityTypeIdentifierWalkingHeartRateAverage
- HKQuantityTypeIdentifierAppleExerciseTime
- HKQuantityTypeIdentifierAppleStandTime
- HKQuantityTypeIdentifierActiveEnergyBurned
- HKQuantityTypeIdentifierEnvironmentalAudioExposure
- HKQuantityTypeIdentifierDietaryEnergyConsumed

### Devices

The DeviceFactory will extract data provided in HKObject device and sourceRevision properties to create a Device Resource. No configuration is required for this conversion.

## Adding support for new conversions

HealthKitToFhir uses JSON configuration files to provide additional data required to perform conversions from HealthKit HKObjects to FHIR Resources. The [DefaultObservationFactoryConfig.json](Sources/Configuration/DefaultObservationFactoryConfig.json) contains conversion data for the [ObservationFactory](Sources/Factories.ObservationFactory.swift) class to support the types listed above.

The example below shows data used for converting an HKQuantitySample containing a Blood Glucose reading to a FHIR Resource. The HKObject type identifier is used to look up data required to populate the Observation, this includes the code and valueQuantity properties of the Blood Glucose Observation. This "static" data will be "copied" to the Observation during the conversion process, while values like the measurement, date, and identifier will be converted from properties of the HKObject.

```json
"HKQuantityTypeIdentifierBloodGlucose": {
        "code": {
            "coding": [
                {
                    "system": "http://loinc.org",
                    "code": "41653-7",
                    "display": "Glucose Glucometer (BldC) [Mass/Vol]"
                }
            ]
        },
        "valueQuantity": {
            "unit" : "mg/dL",
            "system" : "http://unitsofmeasure.org",
            "code" : "mg/dL"
        }
    }
```

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

There are many other ways to contribute to the HealthKitToFhir Project.

* [Submit bugs](https://github.com/Microsoft/healthkit-to-fhir/issues) and help us verify fixes as they are checked in.
* Review the [source code changes](https://github.com/Microsoft/healthkit-to-fhir/pulls).
* [Contribute bug fixes](CONTRIBUTING.md).

See [Contributing to HealthKitToFhir](CONTRIBUTING.md) for more information.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

FHIR® is the registered trademark of HL7 and is used with the permission of HL7.
