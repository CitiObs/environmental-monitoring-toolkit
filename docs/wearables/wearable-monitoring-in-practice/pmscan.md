---
icon: paste
---

# PMScan

## Connecting the cookbook principles in one application

PMScan provides a practical illustration of the needs discussed in this chapter: recording measurements during everyday activities, documenting their context, interpreting personal exposure and deciding which observations contribute to a group. The following example connects these needs to the application’s design choices and explains the limits that remain relevant when using its outputs.

The solution comprises a sensor connection, a mobile application and account-based services for groups and synchronisation. A recording session is called a mission. Participants can record missions, review their observations and choose whether a mission contributes to their active group.

## Connecting a portable sensor to a usable recording system

The deployment questions in this chapter emphasise that a wearable system includes more than the sensor. PMScan illustrates the supporting role of a phone application: connecting the instrument, organising sessions and retaining records that can be reviewed and exported.

The application is built with React and TypeScript, with Capacitor integration for mobile functions such as Bluetooth Low Energy and geolocation. Android and iOS platform dependencies are present in the codebase; compatibility with a particular phone, operating-system version and sensor must be checked for the intended deployment.

The measurement model supports PM1, PM2.5 and PM10 concentrations. Additional fields include temperature, relative humidity, pressure and TVOC when supplied by the connected device. These fields describe the application’s data model; they do not mean that every compatible sensor measures every parameter. Sensor accuracy, response time and detection limits remain properties of the selected instrument.

Missions combine time-stamped measurements, recording duration, available geographical coordinates and context labels. The application includes local storage and account synchronisation. Mission data can be exported as CSV, including measurement, location and context fields; analysis views also provide PDF reporting. Availability of online group and synchronisation functions depends on the associated services.

## Making measurements meaningful through context

During a mission, participants can update both a place category and an activity label. The place category describes the setting, such as home, work or transport; the activity describes what is happening, such as cooking, walking or cleaning. These labels are stored alongside the measurements and timestamps.

Geolocation supplies geographical context when available. Activity and place annotations remain useful indoors or wherever GPS is uncertain: coordinates alone cannot explain a peak or identify the circumstances of exposure. The combined record helps distinguish changes associated with activities, environments and journeys, while retaining the need for interpretation and measurement-quality checks.

## Giving participants a common campaign framework

Comparable observations require participants to describe their situations using a shared vocabulary. PMScan addresses this organisational need through campaign groups and their common settings.

Participants can join a campaign group through an invitation, including a link or QR code. Selecting an active group loads its configured place and activity categories, concentration bands and alert settings. Activities can be organised within place categories, allowing a campaign to define a vocabulary suited to its objectives.

This configuration supports consistent annotation across participants and reduces individual setup. Concentration classifications and activity classifications serve different purposes: one describes measurement ranges; the other describes context. Group thresholds are campaign settings whose meaning and averaging period should be explained, rather than assumed to be medical warnings or regulatory limits.

## Separating personal recording from group contribution

Individual exposure monitoring and contribution to a community dataset are different uses of the same recording. PMScan makes this distinction visible through a mission-level sharing choice.

The mission-saving dialogue includes a sharing control. A mission saved with sharing enabled in group mode is associated with the active group and can contribute to its collaborative views. Participants can also save missions without selecting group sharing.

The sharing choice concerns contribution to the group; it is separate from personal account storage and synchronisation. A mission not shared with a group may still be synchronised to the participant’s account. In the current implementation, the sharing control can already be enabled when group mode is active, so its state should be made clear before a mission is saved. Group sharing should not be equated with unrestricted publication on the internet.

## Moving from individual observations to collective interpretation

The interpretation questions call for views that help participants investigate their observations. PMScan connects personal time series and maps with a collective geographical view of selected contributions.

Mission views combine maps and time-series graphs, while contextual analysis relates measurements to recorded activities and places. Together, these views help participants investigate where values changed, what they were doing and which observations deserve further discussion.

The collaborative map aggregates shared group observations into geographical cells. It presents PM concentrations together with measurement and contributor counts, supporting discussion of patterns across the monitored area. Cell values reflect the available observations: differences in sampling time, coverage, participant behaviour and sensor performance still matter when comparing locations.

## Turning concentration records into exposure indicators

The chapter distinguishes a measured concentration from exposure accumulated over time. PMScan illustrates how these quantities can be summarised, and how estimating inhaled dose introduces an additional assumption about breathing.

PMScan includes complementary ways to summarise personal measurements. Mean concentration is expressed in µg/m³. Time-integrated exposure combines concentration and duration and is expressed in µg·h/m³. Contextual views use this quantity to compare the contribution of recorded activities or places over the selected period.

The application also contains an estimated inhaled-dose calculation for particulate matter: concentration (µg/m³) × duration (h) × assumed inhalation rate (m³/h), giving an estimated mass in µg. The inhalation rate is selected from an activity-based lookup, with fallback assumptions when the context is unknown. It is not a measurement of the participant’s breathing, and the result is not a measured deposited dose in the lungs.

These indicators support exploration and comparison, provided that the pollutant, monitored duration, coverage and assumptions are made explicit. Estimated dose depends on the chosen inhalation rate and activity classification. Gaps, non-wear periods and mixed-activity missions can affect the result; the outputs should not be presented as clinical measurements or individual health-risk predictions.

## Reducing spatial detail in shared outputs

Wearable trajectories can reveal personal routines. PMScan illustrates one response to this concern: reducing the spatial detail of the collaborative representation, while recognising that this does not resolve every data-protection requirement.

PMScan implements spatial generalisation using geohashes. A geohash represents a geographical cell, and its precision determines the area represented. The group can configure the precision used by the collaborative map, allowing observations to be combined into broader areas instead of showing each exact GPS position on that map.

This obfuscation reduces the spatial detail displayed in the collective view. It involves a practical trade-off: larger cells conceal more local detail but also smooth environmental variation. Original coordinates remain in the underlying measurement records; the map’s reduced precision is therefore not, by itself, a guarantee of anonymity or protection across every access and export route.

For a GDPR-aligned deployment, the campaign must define the data controller, purposes, lawful basis, access roles, retention period and procedures for participant rights. Sharing controls and spatial generalisation can support this framework, but do not establish compliance on their own. Timestamps, repeated journeys and contextual annotations must also be considered when assessing whether a person could be identified.

## What this example illustrates

PMScan brings the cookbook’s emphasis on context into the recording and interpretation process. Groups provide shared categories, participants document their situations, personal views support reflection, and selected observations contribute to collaborative maps. Its value lies in connecting measurement with context and participation while making the distinctions between concentration, exposure, estimated dose and data-sharing choices explicit.

### Data protection references

[European Commission guidance on personal data processing](https://commission.europa.eu/law/law-topic/data-protection/information-business-and-organisations/principles-gdpr_en)

[Data Protection Commission guidance on anonymisation and pseudonymisation](https://www.dataprotection.ie/en/dpc-guidance/anonymisation-pseudonymisation)

## Wearable monitoring in practice with the CitiObs PMScan to STAplus App

### From a personal recording to an interoperable observation

The CitiObs PMScan to STAplus App, developed by project partners, illustrates another part of the wearable monitoring workflow: carrying observations from a portable sensor into a shared data infrastructure without losing their measurement context. The iOS application receives readings from a PMScan sensor over Bluetooth, stores recordings on the phone and subsequently uploads selected recordings to a CitiObs STAplus server.

Where the preceding PMScan example highlights contextual interpretation and campaign participation, this example makes the recording and transfer process particularly explicit. It shows how sensor values, time, location, activity, ownership and reuse conditions can travel together as structured observations.

### Choosing how to collect observations in the field

The deployment section stresses that recording settings should match the monitoring question. Here, participants can select a sensor sampling interval of 1, 5, 10 or 30 seconds, or 1 or 5 minutes. The application displays PM1, PM2.5 and PM10 concentrations in µg/m³, temperature in °C and relative humidity, together with the last update time and sensor battery status.

Connecting the sensor sets its clock and starts its measurement cycle; saving a recording is a separate action. Connection-state indicators and a no-data warning help participants recognise interruptions. Bluetooth background operation and background location during recording support collection when the application is not on screen. If the sensor disconnects, recording stops automatically. This makes the interruption explicit, although it does not replace checks for missing data or correct wearing position.

### Keeping activity and environment alongside each sample

As explained in the context section, the same concentration may have different meanings in different situations. Before recording, the participant selects INDOOR or OUTDOOR, and can change this environment label during the recording. An activity picker provides walking, smoking, cooking, sleeping and sitting labels. Each stored sample combines the readings with its time, available GPS position, environment and activity.

Participants can create a named Track with a description, or choose Observations only. A Track provides a way to keep a journey or session together; observations-only recording retains individual samples without that additional grouping. The location display indicates when there is no GPS fix, reminding the user that a valid sensor reading does not necessarily have a reliable geographical position.

### Separating collection from the decision to transfer

The sharing discussion distinguishes recording from making data available elsewhere. This application implements that separation through local recording followed by an explicit upload step. Recordings are saved as JSON files on the phone using iOS file protection; recorded measurement data are not sent to the STAplus server during collection.

An upload list shows pending, uploading, uploaded and failed recordings. The participant selects which recordings to transfer and chooses a reuse licence from the list supplied by the server. Progress is displayed for each recording, and failed uploads can be retried. Local recordings can be deleted, including those already uploaded. Deleting a local copy should not be understood as deleting its server counterpart.

If the application is terminated, an unfinished recording is closed on the next launch, and an interrupted upload is marked as failed for retry. These mechanisms illustrate how a wearable workflow can make unfinished collection and transfer states visible rather than leaving participants uncertain about what has been saved.

### Preserving meaning when measurements enter STAplus

The data-integration section emphasises that transferable observations require more than a list of numbers. During upload, the application creates or reuses the necessary user, device, sensor and measurement-location records, together with a separate data stream for each of the five measured variables. WMO, EnvThes or QUDT definitions identify the measured quantities.

Each sample becomes an ObservationGroup containing its five observations. When a Track was selected, those observations are also linked to it and the Track receives start and end times. Activity records are linked to the measurement location. In this way, simultaneous readings remain associated and their context remains available for subsequent processing. An ObservationGroup is a data grouping, not a participant or campaign group.

The upload workflow reuses a measurement location while movement remains below 10 metres and the environment label is unchanged. This is a location-management rule, not a claim of 10-metre GPS accuracy or a privacy guarantee.

### Supporting geographical exploration without assuming anonymity

The application attaches an H3 grid-cell identifier at resolution 9 to each observation, calculated on the phone. This supplies a common spatial reference for downstream grouping or mapping. A link to the PMScan Viewer provides access to the associated web-map interface.

This spatial indexing serves a different role from the configurable geohash generalisation described in the preceding PMScan example. Adding an H3 cell identifier does not itself establish that precise coordinates are removed or hidden from other users. Access to locations, viewer visibility and any additional privacy transformations must be specified separately.

### Connecting identity and reuse conditions to responsible sharing

The application uses Authenix, the CitiObs identity provider, for sign-in. It checks the identity token’s issuer, audience and expiry, stores tokens in the iOS Keychain and renews the session as needed. Logout disconnects the sensor, stops location collection and resets the server connection. Links provide access to terms and privacy information and the Authenix authorised-apps page.

These features illustrate several building blocks for responsible data handling: protected credentials, an explicit transfer step and a licence associated with reuse. They do not, on their own, define who may read uploaded observations or establish GDPR compliance. As discussed earlier in the cookbook, the deployment still needs clear purposes, access permissions, retention arrangements and procedures for participant rights. A reuse licence is also distinct from the lawful basis for processing personal data.

### What this example illustrates

The CitiObs PMScan to STAplus App demonstrates how a wearable campaign can connect field collection to interoperable data publication: participants configure recording, document context, retain data locally and choose recordings and a licence for transfer. The resulting STAplus observations preserve relationships between readings, locations, activities and tracks. This complements the preceding example by showing the practical steps that make personal measurements available for subsequent analysis and visualisation.
