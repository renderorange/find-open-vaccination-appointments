# NAME

find-open-vaccination-appointments - find open vaccination appointments at HEB locations

# DESCRIPTION

`find-open-vaccination-appointments` is a script to check HEB for open
vaccination appointment slots in Texas.

`find-open-vaccination-appointments` downloads the availability data
from HEB every 20 seconds, then checks the wanted locations for
available appointment slots.

Location, signup URL, and number of availability appointment times and
slots, are output when an availability is found.

This script is a rewrite of @georgebohnisch's nodejs script, in Perl.

# SYNOPSIS

    find-open-vaccination-appointments [--city <houston>] [--city <cypress>]
                                       [--no-respect]
                                       [--help]

# OPTIONS

- --city

    city to get locations from

    multiple city options may be defined

- --no-respect

    get the data every 5 seconds instead of every 20

- --help

    print this dialogue

# EXAMPLES

- check for slots in 2 cities every 5 seconds

        $ ./find-open-vaccination-appointments --city houston --city cypress --no-respect
        [1614970316][info] ctrl+c to exit
        [1614970316][info] new appointment data available
        [1614970316][info] open appointment slot found:
        $VAR1 = {
                  'city' => 'HOUSTON',
                  'latitude' => '29.92325',
                  'longitude' => '-95.19697',
                  'name' => 'Summerwood Market H-E-B',
                  'openAppointmentSlots' => 1,
                  'openTimeslots' => 1,
                  'slotDetails' => [
                                     {
                                       'manufacturer' => 'Moderna',
                                       'openAppointmentSlots' => 1,
                                       'openTimeslots' => 1
                                     }
                                   ],
                  'state' => 'TX',
                  'storeNumber' => 614,
                  'street' => '12680 W.LAKE HOUSTON PKWY 8',
                  'type' => 'store',
                  'url' => 'https://heb.secure.force.com/FlexibleScheduler/FSAppointment?event_ID=[removed]',
                  'zip' => '77044-6087'
                };
        [1614970316][info] open appointment slot found:
        $VAR1 = {
                  'city' => 'CYPRESS',
                  'latitude' => '29.9925',
                  'longitude' => '-95.74599',
                  'name' => 'Fairfield Market H-E-B',
                  'openAppointmentSlots' => 1,
                  'openTimeslots' => 1,
                  'slotDetails' => [
                                     {
                                       'manufacturer' => 'Moderna',
                                       'openAppointmentSlots' => 1,
                                       'openTimeslots' => 1
                                     }
                                   ],
                  'state' => 'TX',
                  'storeNumber' => 656,
                  'street' => '28550 US- 290',
                  'type' => 'store',
                  'url' => 'https://heb.secure.force.com/FlexibleScheduler/FSAppointment?event_ID=[removed]',
                  'zip' => '77433-4288'
                };
        [1614970364][info] new appointment data available
        [1614970428][info] new appointment data available
        [1614970491][info] new appointment data available

# DEPENDENCIES

- [Getopt::Long](https://metacpan.org/pod/Getopt%3A%3ALong)
- [Pod::Usage](https://metacpan.org/pod/Pod%3A%3AUsage)
- [HTTP::Tiny](https://metacpan.org/pod/HTTP%3A%3ATiny)
- [Try::Tiny](https://metacpan.org/pod/Try%3A%3ATiny)
- [JSON::Tiny](https://metacpan.org/pod/JSON%3A%3ATiny)
- [Test::Deep::NoTest](https://metacpan.org/pod/Test%3A%3ADeep%3A%3ANoTest)
- [Data::Dumper](https://metacpan.org/pod/Data%3A%3ADumper)
