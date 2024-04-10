# 20240410 - Securely connect Demo Badge to the AWS cloud - Embedded World

```
Securely connect Demo Badge to the AWS cloud
EVENT OPENS IN
0d 14h 54m 23s
REGISTRATION CONFIRMED

    M
    Marcel Petrick
    Price
    $30.00
    Not Marcel Petrick ? Click here

EVENT DETAILS

    When
    Wednesday, April 10, 2024 · 2:00 p.m.
    Paris (GMT +2:00)

    Add to calendar
    About
    Date: Wednesday April 10, 2024
    Start Time: 2:00 PM local Germany time
    Where: Nuremberg Messe, NCC Mitte, Munchen 2
    Duration: Three hours

    Cost to attend: $30US (approximately 27 Euros)

    Are you looking to accelerate your IoT product development time and want to quickly build a connected solution in just few weeks?

    In this workshop, you will get hands-on experience and explore how to securely connect IoT products and manage them with AWS IoT services. Using a purpose-built educational device, the Demo Badge, you will learn about different AWS IoT connectivity options, including the MQTT protocol on AWS IoT Core and Bluetooth Low Energy on the Amazon Sidewalk network. This workshop also introduces you to use cases, such as, over-the-air updates, sensor data ingestion, geo-location lookup, digital twins and shadows, and low-power connectivity.

        Connecting IoT devices using MQTT to AWS Cloud
        Security, Certificates, device onboarding using AWS IoT ExpressLink
        OTA Updates
        Sensor Data Ingestion using Amazon Timestream and Grafana
        Device control and digital twins with mobile app integration

    Who should attend?
        Hardware and platform developers who need to enable ‘connectivity’ technologies in their design
        Firmware engineers who want to onboard a connected solution to the cloud with just few lines of code

    Giveaway
        The Demo device will be provided to each attendee to take with them and practice at your own pace
        The attendee will be able to reuse the Demo Badge for connecting to AWS IoT and conducting proofs-of-concept

    HW/SW requirements – what attendees will need to do prior to Workshop
        A laptop + power supply running Windows/macOS/Linux
        Google Chrome browser
        Administrator privileges to access USB devices on your laptop

    Agenda
        10 min - introduction
        20 min - presentation
        2 hour - self-paced working with support staff

    Speakers
        Thomas Kriechbaumer and Andrzej Mizerkiewicz -
        Senior IoT Solutions Architect at AWS
        Support staff - 3-4 IoT Solutions Architects

    Price
    $30.00
    Language
    English
    OPEN TO
    Open to developers on a first come, first served basis, up to 40 registrants. We have the right to refuse participation after registration and payment is received and a credit will be given.
    Dial-in available
    (listen only)
    Not available.

FEATURED PRESENTERS

    Webinar hosting presenter
    Thomas Kriechbaumer
    Senior IoT Solutions Architect at AWS
    Full Profile
    Webinar hosting presenter
    Andrzej Mizerkiewicz
    Senior IoT Solutions Architect at AWS
    Full Profile
```

## intro
* thomas kriechbaumer started
* help and educate the customer to build the next product or services
* agenda: presentation 30 min, uided walk through 2 hours, open discussion 30 minutes
* loud: it-ressources on demand
* things linke iot-services are cloud as well; lots of flexibility; and danymic allocation
* traditional: on premise stuff
*  by 2030 29 bio devices are expected
* common challenges of connected products:
  * turning data into value
  * deploying connected devices
  * managing and scaling large fleets
  * managing security and privacy
* a prototype is done in 5 minutes, but rolling out i hundreads ofthrousands needs more effort

## AW ressources
* AWS IoT Core; like an MQTT broker - fully compliant, MQTT 3 and 5; securely and privately wrapped
  * use publish and subscribe capabilities
* attach to the broker rules and actions
* if something matches a topic it should be routed and forwarded to a specific point
* AWS IoT Core is a fully managed server; not needed to write any specific code, already provided
* Amazon Sidewalk network: community aspect
* also: MAtter devices - local communication 8device to device)
* LoRaWAN
* DemoBade is purpose-built:
  * run through all typical aspects of the lifecycle
  * has microcontroller
  * has color TFT display, several sensors
  * AWS IoT ExpressLink module as link to the cloud with wifi-technology
  * expresslink is certified and qualified

## topics
* introduction to MQTT with publish/subscribe
* sensor data ingestion
* device location using wifi scanning
* digital twin and shadow
* image transfer using over the air updates
* optional: low poer connectivitiy with amazon sidewalk


* amazon geolocation feature?can use for instance ssid/mac-adress to give some idea where you are
* our devices are in a "workshop" mode; can be turned off later
*
