---
icon: paste
---

# CitiObs PMScan to STAplus App

## From a personal recording to an interoperable observation

The CitiObs PMScan to STAplus App, developed by project partners, illustrates another part of the wearable monitoring workflow: carrying observations from a portable sensor into a shared data infrastructure without losing their measurement context. The iOS application receives readings from a PMScan sensor over Bluetooth, stores recordings on the phone and subsequently uploads selected recordings to a CitiObs STAplus server.

Where the preceding PMScan example highlights contextual interpretation and campaign participation, this example makes the recording and transfer process particularly explicit. It shows how sensor values, time, location, activity, ownership and reuse conditions can travel together as structured observations.

## Choosing how to collect observations in the field

The deployment section stresses that recording settings should match the monitoring question. Here, participants can select a sensor sampling interval of 1, 5, 10 or 30 seconds, or 1 or 5 minutes. The application displays PM1, PM2.5 and PM10 concentrations in µg/m³, temperature in °C and relative humidity, together with the last update time and sensor battery status.

Connecting the sensor sets its clock and starts its measurement cycle; saving a recording is a separate action. Connection-state indicators and a no-data warning help participants recognise interruptions. Bluetooth background operation and background location during recording support collection when the application is not on screen. If the sensor disconnects, recording stops automatically. This makes the interruption explicit, although it does not replace checks for missing data or correct wearing position.

## Keeping activity and environment alongside each sample

As explained in the context section, the same concentration may have different meanings in different situations. Before recording, the participant selects INDOOR or OUTDOOR, and can change this environment label during the recording. An activity picker provides walking, smoking, cooking, sleeping and sitting labels. Each stored sample combines the readings with its time, available GPS position, environment and activity.

Participants can create a named Track with a description, or choose Observations only. A Track provides a way to keep a journey or session together; observations-only recording retains individual samples without that additional grouping. The location display indicates when there is no GPS fix, reminding the user that a valid sensor reading does not necessarily have a reliable geographical position.

## Separating collection from the decision to transfer

The sharing discussion distinguishes recording from making data available elsewhere. This application implements that separation through local recording followed by an explicit upload step. Recordings are saved as JSON files on the phone using iOS file protection; recorded measurement data are not sent to the STAplus server during collection.

An upload list shows pending, uploading, uploaded and failed recordings. The participant selects which recordings to transfer and chooses a reuse licence from the list supplied by the server. Progress is displayed for each recording, and failed uploads can be retried. Local recordings can be deleted, including those already uploaded. Deleting a local copy should not be understood as deleting its server counterpart.

If the application is terminated, an unfinished recording is closed on the next launch, and an interrupted upload is marked as failed for retry. These mechanisms illustrate how a wearable workflow can make unfinished collection and transfer states visible rather than leaving participants uncertain about what has been saved.

## Preserving meaning when measurements enter STAplus

The data-integration section emphasises that transferable observations require more than a list of numbers. During upload, the application creates or reuses the necessary user, device, sensor and measurement-location records, together with a separate data stream for each of the five measured variables. WMO, EnvThes or QUDT definitions identify the measured quantities.

Each sample becomes an ObservationGroup containing its five observations. When a Track was selected, those observations are also linked to it and the Track receives start and end times. Activity records are linked to the measurement location. In this way, simultaneous readings remain associated and their context remains available for subsequent processing. An ObservationGroup is a data grouping, not a participant or campaign group.

The upload workflow reuses a measurement location while movement remains below 10 metres and the environment label is unchanged. This is a location-management rule, not a claim of 10-metre GPS accuracy or a privacy guarantee.

## Supporting geographical exploration without assuming anonymity

The application attaches an H3 grid-cell identifier at resolution 9 to each observation, calculated on the phone. This supplies a common spatial reference for downstream grouping or mapping. A link to the PMScan Viewer provides access to the associated web-map interface.

This spatial indexing serves a different role from the configurable geohash generalisation described in the preceding PMScan example. Adding an H3 cell identifier does not itself establish that precise coordinates are removed or hidden from other users. Access to locations, viewer visibility and any additional privacy transformations must be specified separately.

## Connecting identity and reuse conditions to responsible sharing

The application uses Authenix, the CitiObs identity provider, for sign-in. It checks the identity token’s issuer, audience and expiry, stores tokens in the iOS Keychain and renews the session as needed. Logout disconnects the sensor, stops location collection and resets the server connection. Links provide access to terms and privacy information and the Authenix authorised-apps page.

These features illustrate several building blocks for responsible data handling: protected credentials, an explicit transfer step and a licence associated with reuse. They do not, on their own, define who may read uploaded observations or establish GDPR compliance. As discussed earlier in the cookbook, the deployment still needs clear purposes, access permissions, retention arrangements and procedures for participant rights. A reuse licence is also distinct from the lawful basis for processing personal data.

## What this example illustrates

The CitiObs PMScan to STAplus App demonstrates how a wearable campaign can connect field collection to interoperable data publication: participants configure recording, document context, retain data locally and choose recordings and a licence for transfer. The resulting STAplus observations preserve relationships between readings, locations, activities and tracks. This complements the preceding example by showing the practical steps that make personal measurements available for subsequent analysis and visualisation.
