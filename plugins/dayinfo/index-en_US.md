# Information of the day

## Presentation

This plugin makes it possible to obtain several types of equipment which provide their information commands:

* Holidays

* School vacation

* Moon

* Miscellaneous information (season and weekend)

* Personalized calendar


## Commands available

### Bank holidays

* current holiday (1 or 0)

* number of days before the next public holiday

### Various information

* current season ('Winter', 'Spring', 'Summer', 'Fall')

* number of days before next season

* current weekend (1 or 0)

* day of the year (0 to 365)

### School vacation

* current vacation (1 or 0)

* holiday label (as defined in the calendar provided)

* number of days before the next vacation

* number of days before the end of the next vacation

* label next vacation

### Moon

* moon phase (value from 0 to 1, 0 and 1 being new moon, full moon 0.5)

* age of the moon (in days)

* brightness

* distance

* name of the phase

### Personalized calendar

* current event (1 or 0)

* event label (as defined in the calendar provided)

* number of days before the next event

* number of days before the end of the next event

* label next event

## Configuration

The plugin does not have a general configuration.

On the equipment, you must configure the type and location if necessary

For the personalized calendar, a field is used to fill in the path, this file must be local in ics format, the calendar must contain events of type "whole days" with a start and an end. For example a calendar of holidays, school holidays not supported as standard, holidays, etc.

## FAQ

> Does the plugin rely on third-party APIs?

No, including school holiday calendars are included locally.

> Can I get a calendar from a Nextcloud instance?

Not directly in the plugin, but via this kind of command yes:

wget --output-document ./calendar.ics --auth-no-challenge --http-user = USER --http-password = "PASSWORD" "http: // IP: PORT / remote.php / dav / calendars / USER / Kalender? Export "

## Changelog

[See the dedicated page] (changelog-en_US.md).
