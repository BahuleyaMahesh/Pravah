# PRAVAH
------------------------------------------------------------------------

## 1. Project at a glance

**GATIQ** is a multilingual, two-sided freight coordination platform
that connects food suppliers with transport providers. It uses
AI-assisted intake, perishability-aware prioritisation, vehicle/cargo
compatibility checks, route and load optimisation, driver-controlled
trip offers, return-load matching, recurring bookings, and journey
monitoring to make fragmented rural freight more efficient.

The central idea is not simply to build another truck-booking app. GATIQ
should help coordinate fragmented shipments and underused vehicle
capacity as a connected logistics network.

### Core proposition

-   **For suppliers:** Find suitable transport for food products based
    on cargo requirements, quantity, location, urgency, timing, route,
    and price.
-   **For transport providers:** Receive relevant trip offers, use
    available capacity, find compatible return loads, and choose which
    jobs to accept.
-   **For FPOs, aggregators and fleet coordinators:** Coordinate
    multiple suppliers and vehicles through an assisted dashboard.
-   **For the network:** Reduce avoidable empty kilometres, improve
    vehicle utilisation, and help time-sensitive food reach its
    destination on time.

### Suggested tagline

**Smarter Freight. Less Waste. Better Connectivity.**

### Important naming note

GATIQ is the current project/team/product working name. Check name
availability and trademark conflicts before public commercial use. The
product name and team name can be changed independently.

------------------------------------------------------------------------

## 2. Competition context and project objective

The team selected **Tech4Bharat 2026 Problem Statement 5.3 --- Rural
Freight**.

The challenge is understood as addressing rural freight inefficiency:
fragmented demand, partially loaded vehicles, empty return journeys,
delays, high transport costs, and difficulty coordinating small
suppliers with local transport providers.

The project should respond to the challenge through a practical,
measurable system---not just a chatbot or a conventional listing
marketplace.

### What the prototype must prove

1.  A supplier can create a structured food shipment using a form or
    voice conversation.
2.  A transport provider can register vehicles, drivers, specifications,
    routes and availability.
3.  The system can reject unsuitable vehicles and identify feasible
    transport options.
4.  The system can prioritise time-sensitive shipments without violating
    cargo-suitability constraints.
5.  The system can consolidate compatible shipments and calculate
    remaining vehicle capacity across route segments.
6.  Drivers can review a trip offer and accept, reject or counteroffer
    voluntarily.
7.  Suppliers and drivers can communicate after a booking is mutually
    confirmed.
8.  The system can identify suitable return loads and recurring shipment
    opportunities.
9.  The team can compare the proposed approach with a simple baseline
    using clear metrics.

The official challenge brief and current competition rules should be
checked directly by the team before submission. Do not rely on this
README as a substitute for the latest organiser instructions.

------------------------------------------------------------------------

## 3. Users and roles

GATIQ has three main user roles.

### 3.1 Food supplier

Potential users: - Individual farmers. - Farmer Producer Organisations
(FPOs). - Agricultural aggregators. - Wholesalers and distributors. -
Food processors and small food businesses. - Other organisations that
need food transported.

Supplier capabilities: - Register and maintain a profile. - Create a
shipment through a form or voice assistant. - Save shipment templates
for reuse. - Set pickup and delivery locations and time windows. -
Specify food category, quantity, packaging and handling needs. - View
feasible transport options and estimated prices. - Review and confirm a
driver's offer. - View trip status and available location updates. -
Contact the driver after mutual booking confirmation. - Create recurring
shipment schedules. - Report delays, damage, quantity mismatch or other
incidents.

### 3.2 Transport provider

Potential users: - Individual tempo, mini-truck, tractor-trailer and
goods-vehicle owners. - Drivers. - Fleet operators and logistics
companies.

Transport capabilities: - Register one or more vehicles. - Register
drivers and associate each driver with a specific vehicle/trip. -
Specify payload, cargo volume, dimensions, body type and equipment. -
Set current location, service regions, preferred routes and
availability. - Declare current cargo and remaining capacity. - Set
departure and return windows. - Receive trip offers with cargo, route,
stops, time windows and proposed payout. - Accept, reject or
counteroffer. - Update trip status and share location when permitted. -
Confirm pickup and delivery. - View return-load opportunities. - Accept
or decline recurring work arrangements.

**Important:** A fleet with eight drivers and five vehicles does not
automatically have eight available vehicles. Driver availability,
vehicle availability and their assignment must be represented
separately.

### 3.3 FPO / fleet / dispatcher coordinator

This role is important for rural adoption and assisted access.

A coordinator can: - Create shipments on behalf of farmers who do not
use smartphones. - Manage multiple suppliers or vehicles, subject to
permissions. - Help users complete voice or assisted bookings. - Monitor
shipment and fleet status. - Resolve missing information and coordinate
changes.

The platform should not assume that every farmer or driver is
comfortable navigating a complex smartphone application.

------------------------------------------------------------------------

## 4. Food and shipment model

The supplier flow should use clear food categories. Avoid the ambiguous
phrase "free food" when referring to unpackaged produce.

### 4.1 Food categories

Initial categories: 1. **Fresh / loose produce:** vegetables, fruits,
grains and similar agricultural produce. 2. **Packaged / processed
food:** packaged snacks, ingredients, processed foods and similar goods.
3. **Prepared / cooked food:** food that may require specific handling
and delivery windows. 4. **Other food products:** a fallback category
with a request for details.

The category determines which additional questions the application asks.

### 4.2 Shipment information

A shipment record should capture as many of the following as relevant:

  -----------------------------------------------------------------------
  Field                               Example / explanation
  ----------------------------------- -----------------------------------
  Shipment ID                         Unique system-generated identifier

  Supplier ID                         User or organisation creating the
                                      request

  Product                             Tomatoes, paneer, packaged snacks,
                                      etc.

  Food category                       Fresh, packaged, prepared or other

  Quantity                            450 kg

  Quantity confidence                 Estimated or verified

  Package count                       30 crates

  Package type                        Crate, sack, carton, pallet, loose

  Individual package weight           15 kg

  Estimated volume                    Cubic metres or package dimensions

  Origin                              Village, collection point or
                                      coordinates

  Destination                         Mandi, processor, warehouse or
                                      buyer

  Ready time                          Earliest pickup time

  Latest pickup                       Latest acceptable collection time

  Delivery deadline                   Required arrival time

  Maximum acceptable transit time     If known and applicable

  Temperature range                   Only where required and known

  Refrigeration requirement           Required / not required / unknown

  Covering                            Open, covered, waterproof cover,
                                      etc.

  Ventilation                         Required / not required / unknown

  Food-grade requirement              Based on product and applicable
                                      rules

  Fragility / stacking                Handling and loading restrictions

  Cargo compatibility                 Products that may or may not travel
                                      together

  Special instructions                Free-text and voice notes

  Status                              Draft, submitted, matching,
                                      offered, booked, picked up,
                                      delivered, cancelled, etc.
  -----------------------------------------------------------------------

The application should distinguish **estimated weight** from **verified
weight**. An LLM must never silently invent a weight, location,
temperature range, deadline or other operational value.

### 4.3 Dynamic shipment forms

The supplier should not have to answer irrelevant questions. For
example: - A shipment requiring refrigeration should trigger temperature
and equipment questions. - Loose vegetables may need crate, ventilation
and covering information. - Packaged food may need carton count,
stacking and handling details. - Prepared food may require a tighter
collection/delivery window.

When a required field is missing, the voice assistant or form should ask
for it. Unknown values should remain explicitly unknown until confirmed.

------------------------------------------------------------------------

## 5. Voice-first, multilingual interaction

Voice interaction is a core product requirement, not an optional
decoration.

Local suppliers and drivers may be uncomfortable typing into a mobile
application. GATIQ should let users speak naturally in a supported
regional language, receive spoken follow-up questions, and confirm the
resulting structured record.

### 5.1 Voice conversation flow

Example supplier utterance:

> "I have 450 kilos of tomatoes ready in Village A tomorrow morning. I
> need them at the mandi before 11."

The voice assistant should: 1. Detect the language and transcribe
speech. 2. Extract candidate fields such as product, quantity, origin,
pickup date/time and destination/deadline. 3. Identify missing or
ambiguous fields. 4. Ask one focused follow-up question at a time. 5.
Read back the interpreted shipment. 6. Let the user correct any field.
7. Create the shipment only after confirmation. 8. Show the structured
record as a table/card in the application.

Example follow-up: - "Are the tomatoes packed in crates or loose?" -
"Which village should the vehicle collect them from?" - "Is 11 AM the
latest delivery time?"

### 5.2 Voice interaction for drivers

Drivers should be able to speak to the assistant to: - Register or
update vehicle availability. - Declare current cargo and remaining
capacity. - Set destination and return availability. - Hear a trip
offer. - Ask for the proposed route, stops, payout and delivery time. -
Accept, reject or counteroffer. - Report pickup, delay, breakdown or
delivery. - Ask whether there are compatible return loads.

The driver must explicitly confirm consequential actions such as
accepting a trip, changing a destination or confirming a booking. Voice
recognition alone must not be treated as consent.

### 5.3 Interaction design

The experience should feel like a simple phone conversation: -
Local-language speech input and spoken responses. - Short, clear
questions. - One missing detail at a time. - Read-back confirmation. -
Easy correction and cancellation. - Visible text/table summary for
review. - A non-voice fallback for noisy environments or
speech-recognition failure. - Human-assisted booking through an
FPO/coordinator where needed.

### 5.4 Proposed language technology

Investigate: - Bhashini services for speech recognition, translation and
text-to-speech. - AI4Bharat models such as IndicConformer and
IndicTrans2, subject to their current availability, licences and
integration requirements.

**Initial language scope:** Kannada and English. Hindi and Tamil can
follow if time and integration access permit.

Do not make the entire prototype dependent on an external voice API.
Build a text-based fallback and a seeded demo conversation in case API
credentials, quotas, network connectivity or language accuracy become
blockers.

------------------------------------------------------------------------

## 6. Saved shipments and reusable templates

Suppliers should not need to re-enter the same shipment details every
time.

At the end of a successful shipment creation flow, offer: - **Save as
template** - **Use once** - **Schedule recurring shipment**

A saved template can contain: - Product and category. - Typical
quantity. - Packaging. - Handling requirements. - Origin and
destination. - Preferred pickup/delivery windows. - Special
instructions. - Preferred transporter, if applicable.

When reusing a template, the system should show the saved values and ask
the supplier to confirm what may have changed, especially quantity,
date, readiness, destination and handling condition.

A saved template is not a live shipment and should not automatically
create a booking.

------------------------------------------------------------------------

## 7. Recurring shipments and scheduled driver arrangements

Recurring shipments are a core requirement.

Example: - 30 kg tomatoes. - Every Monday. - Pickup at 7:00 AM. - Same
origin and destination. - A preferred driver who has agreed to the
recurring arrangement.

### 7.1 Recurring schedule fields

-   Shipment template ID.
-   Recurrence frequency: daily, weekly, monthly or custom.
-   Day(s) of week or date rule.
-   Pickup time/window.
-   Delivery deadline/window.
-   Start date and optional end date.
-   Expected quantity and permitted variation, if any.
-   Preferred driver or fleet.
-   Backup preference.
-   Supplier confirmation preference.
-   Driver confirmation policy.
-   Holiday/skip rules.
-   Cancellation and rescheduling rules.

### 7.2 Important booking rule

A recurring schedule should **not** silently guarantee that a driver
will attend "without fail." Availability, vehicle condition, illness,
breakdowns, weather and other disruptions can occur.

Instead: 1. Supplier creates the recurring schedule. 2. Preferred driver
reviews and agrees to the recurring arrangement. 3. The system creates
an upcoming trip instance for each occurrence. 4. The driver receives a
reminder/confirmation request before the trip. 5. If the driver
confirms, the trip becomes confirmed. 6. If the driver declines or does
not confirm by the configured cutoff, the system alerts the supplier and
searches for a suitable replacement. 7. Supplier approves any
replacement or material change in price/terms.

The system should distinguish: - A saved shipment template. - A
recurring schedule. - An individual shipment instance. - A confirmed
driver booking.

This separation prevents accidental duplicate or unconfirmed trips.

------------------------------------------------------------------------

## 8. Transport provider and vehicle registry

### 8.1 Fleet-level details

-   Company/fleet name.
-   Contact person.
-   Number of drivers and vehicles.
-   Operating locations.
-   Service areas and regions.
-   Preferred corridors/routes.
-   Operating hours.
-   Fleet coordinator details.

### 8.2 Driver details

-   Driver ID and verified contact details.
-   Assigned vehicle for a trip.
-   Availability and working hours.
-   Preferred routes and destinations.
-   Languages spoken.
-   Consent to location sharing.
-   Trip history and operational status.

Any identity, licence, vehicle registration or insurance verification
should follow applicable law and the prototype's actual verification
capability. Do not label an account "verified" unless the relevant check
has actually occurred.

### 8.3 Vehicle details

  Field                    Explanation
  ------------------------ ------------------------------------------------------
  Vehicle ID               Unique identifier
  Vehicle type             Tempo, mini-truck, tractor-trailer, truck, van, etc.
  Payload capacity         Maximum permitted cargo weight
  Cargo volume             Usable cargo volume
  Internal dimensions      Length, width and height
  Body type                Open, covered, enclosed, refrigerated
  Refrigeration            Available or not
  Temperature capability   Supported range, if verified
  Ventilation              Available configuration
  Covering                 Tarpaulin/waterproof covering, etc.
  Food suitability         Relevant food-grade/hygiene information
  Loading constraints      Crates, sacks, cartons, pallets, stacking
  Current cargo            Existing assigned loads
  Available capacity       Recalculated as goods are picked up/delivered
  Current location         GPS or manually confirmed location
  Availability             Available, reserved, on trip, unavailable
  Route                    Current destination and planned corridor
  Return window            When and where the vehicle can take another load
  Operating cost / quote   Driver or fleet-provided commercial terms

Weight and volume are separate constraints. A vehicle can run out of
space before reaching its payload limit.

Capacity must be calculated for every route segment. When cargo is
delivered, the freed capacity can be reused for a later pickup if the
route and timing remain feasible.

------------------------------------------------------------------------

## 9. Freshness Priority Engine

Perishability-aware prioritisation is one of GATIQ's main
differentiators.

The system should not simply label all vegetables "urgent" and all
packaged goods "normal." Actual urgency depends on product, condition,
storage, harvest/production time, packaging, temperature exposure, route
duration and the supplier's required delivery window.

### 9.1 Inputs

-   Product/food category.
-   Harvest or production time, if known.
-   Current storage conditions.
-   Temperature exposure, where relevant.
-   Packaging and handling.
-   Required temperature range, if applicable.
-   Pickup readiness.
-   Delivery deadline.
-   Maximum acceptable transit time, where known.
-   Predicted journey time and uncertainty.

### 9.2 Time slack

A useful operational concept is:

**Time Slack = Latest Acceptable Arrival − Predicted Arrival**

Lower positive slack means the shipment has less time buffer and may
need higher priority. Negative slack means the proposed journey does not
meet the declared deadline.

Priority can be presented as: - Critical. - High. - Normal.

These are operational urgency labels, not food-safety certifications or
claims about guaranteed shelf life.

### 9.3 Hard safety and compatibility rule

**Urgency must never override vehicle suitability.**

For example, a chilled dairy shipment must not be assigned to an
unsuitable unrefrigerated vehicle simply because it is urgent.

The system should: - Reject or flag incompatible vehicles. - Ask for
missing handling information. - Avoid inventing temperature
requirements. - Use validated rules/data for product handling. - Explain
why a vehicle is unsuitable. - Allow human review when the data is
uncertain.

Weather and traffic can influence journey-risk estimates, but a district
weather warning does not prove that a particular road is closed.

------------------------------------------------------------------------

## 10. Intelligent matching and trip offers

The matching system should use two stages.

### 10.1 Stage 1: Feasibility filtering

Filter out vehicles that cannot safely or practically perform the
shipment.

Hard checks include: - Vehicle and cargo compatibility. - Payload
capacity. - Cargo volume and dimensions. - Temperature/refrigeration
requirements. - Packaging and handling requirements. - Pickup and
delivery time windows. - Driver and vehicle availability. - Route and
road suitability. - Existing trip commitments. - Maximum detour or
travel-time limits.

Do not rank an infeasible vehicle as a good match simply because it is
nearby or cheap.

### 10.2 Stage 2: Ranking feasible options

Rank the remaining options using: - Distance/time to pickup. - Predicted
arrival time. - Remaining weight and volume capacity. - Route
compatibility. - Cost/payout. - Detour. - Perishability urgency and
delivery slack. - Opportunity to consolidate compatible shipments. -
Potential return load. - Driver preferences and acceptance history, once
enough real data exists.

The system should explain its recommendations in plain language, for
example:

> "Driver C is recommended because the vehicle meets the shipment's
> temperature and capacity requirements and can reach the pickup point
> within the requested window, despite being farther away."

### 10.3 Driver-controlled offers

The driver receives: - Product and quantity. - Pickup and delivery
locations. - Required stops. - Proposed route and estimated time. -
Handling requirements. - Existing cargo and remaining capacity. -
Proposed payout and relevant cost details. - Delivery deadline. - Any
return-load opportunity.

The driver can: - Accept. - Reject. - Counteroffer, if enabled.

The supplier reviews and confirms the offer. Contact information is
shared after mutual confirmation, subject to privacy settings and
consent.

Avoid sending the same job indiscriminately to every driver. Use ranked
or controlled batches of offers and expire/withdraw competing offers
when a trip is accepted.

------------------------------------------------------------------------

## 11. Load consolidation and route optimisation

The core technical engine is a constrained vehicle-routing and
pickup-and-delivery optimisation system.

### 11.1 Candidate generation

Find shipments that may be compatible based on: - Geographic
proximity. - Shared or intersecting delivery corridors. - Overlapping
pickup/delivery windows. - Cargo compatibility. - Vehicle capacity. -
Maximum detour. - Perishability and delivery slack.

Nearby shipments are not automatically compatible. The route and
constraints must make sense.

### 11.2 Optimisation model

The problem resembles a heterogeneous Vehicle Routing Problem with
Pickup and Delivery and Time Windows (VRPPDTW).

**Hard constraints:** - Weight capacity on every route segment. - Volume
capacity on every route segment. - Pickup before its paired delivery. -
Pickup and delivery time windows. - Cargo compatibility. - Vehicle/road
suitability. - Driver and vehicle availability. - Existing
commitments. - Voluntary driver acceptance.

**Objectives to minimise:** - Total transport cost. - Empty
kilometres. - Late arrivals. - Excessive detours. - Perishable-goods
delay exposure. - Unserved shipments, with a suitable penalty.

A conceptual objective is:

`Minimise: transport_cost + α(empty_km) + β(late_time) + γ(spoilage_risk) + δ(unserved_shipments)`

The weights should be tuned and evaluated against observed or simulated
scenarios. The model should not hide trade-offs or claim one set of
weights is universally correct.

### 11.3 Recommended implementation

Use: - Python. - Google OR-Tools for routing and constraints. - A
road-network distance/time matrix from a routing service. - A
candidate-generation layer to reduce the number of combinations
considered.

Start with a simple, reliable baseline and then add constraints
incrementally.

------------------------------------------------------------------------

## 12. Return-load / backhaul matching

Backhaul matching is a separate core capability, not just a minor
feature.

Example: - A truck travels Bengaluru → Chennai. - It reaches Chennai and
would otherwise return empty. - GATIQ checks for compatible suppliers in
Chennai and along the return corridor who need goods moved towards
Bengaluru.

Potential pickup areas might include Chennai, Sriperumbudur, Vellore,
Krishnagiri and Hosur, but only if the route, time windows, cargo and
detour constraints make them feasible.

The Backhaul Agent should check: 1. Driver's declared return window. 2.
Vehicle location and availability. 3. Remaining weight and volume
capacity. 4. Compatible return shipments. 5. Pickup and delivery
windows. 6. Route corridor and detour. 7. Cargo handling compatibility.
8. Expected payout and driver's minimum acceptable terms.

The driver chooses whether to accept.

Do not hold a driver indefinitely while waiting for a return load. The
driver declares a departure window and maximum waiting time. If no
suitable load is found, the driver can leave.

A shipment can be picked up and delivered at intermediate points along a
corridor if it remains feasible. Exact city-to-city matching is not
required.

------------------------------------------------------------------------

## 13. Dynamic capacity and rolling-horizon updates

GATIQ should keep vehicle capacity current as a trip progresses.

Example: - Vehicle capacity: 2,000 kg. - Outbound cargo: 1,200 kg. -
Additional pickup: 300 kg. - Remaining weight capacity: 500 kg, subject
to volume and all other constraints.

When a delivery is completed, the cargo is removed from the vehicle's
onboard load and capacity is recalculated for subsequent route segments.

The system should re-optimise when important events occur: - New
shipment request. - Driver cancellation. - Vehicle breakdown. - Shipment
quantity change. - Pickup or delivery completion. - Major delay. -
Driver availability change.

Use a rolling-horizon approach. Already accepted and in-progress
commitments should remain stable unless the affected parties approve
changes. Do not constantly change routes in ways that undermine trust.

------------------------------------------------------------------------

## 14. Cancellation and disruption recovery

If a driver cancels: 1. Mark the vehicle/offer status correctly. 2.
Identify affected shipments. 3. Remove the cancelled vehicle from the
feasible fleet. 4. Re-optimise uncommitted shipments against available
vehicles. 5. Find replacement options. 6. Recalculate route, ETA and
price. 7. Explain the changes to affected suppliers. 8. Obtain approval
for material changes. 9. Notify the replacement driver and confirm the
new booking.

Other disruption cases: - Driver delay. - Breakdown. - Supplier not
ready. - Quantity mismatch at loading. - Destination change. - Poor
weather. - Road restriction or closure report. - Network loss.

The system should preserve an event history and never silently change a
confirmed booking's commercial terms.

------------------------------------------------------------------------

## 15. Pricing and fair cost allocation

The platform should show transparent charges to suppliers and a clear
payout to drivers.

A conceptual trip-cost model may include: - Base charge. - Distance. -
Time. - Tolls. - Handling/loading. - Agreed waiting charges. - Other
disclosed charges.

For consolidated trips, do not simply split the total bill equally.

A proposed allocation approach: - Allocate shared road-segment costs
according to each shipment's capacity use while onboard. - Attribute
additional pickup/drop-off costs to the shipment that requires those
stops. - Attribute waiting costs according to the agreed cause/rule. -
Ensure individual allocations sum exactly to the agreed transporter
payout.

Weight and volume should both be considered when determining capacity
consumption.

Show: - Each shipper's amount. - Shared route segments. - Additional
detour costs. - Total transporter payout. - Estimated standalone
alternative, where available. - Whether the proposed pooled arrangement
actually saves money for that supplier.

Do not claim savings if the pooled option is more expensive for a
participant. The commercial terms should be accepted by the relevant
parties before booking.

Payments, escrow and automated settlement are not required for the first
prototype.

------------------------------------------------------------------------

## 16. Live tracking, communication and delivery proof

### 16.1 Tracking

After a booking is mutually confirmed: - Supplier can see trip status. -
Driver can share location with permission. - Map displays planned route
and available location updates. - ETA is updated where possible. - Last
location update time is visible. - The interface distinguishes live
location from stale/offline location.

A PWA/browser may not reliably provide continuous background GPS when
suspended or offline. For the first prototype, use foreground location
where supported and clearly show the last update time. A native app may
be considered later for more robust background tracking, with explicit
permissions and battery considerations.

### 16.2 Direct communication

After confirmation, supplier and driver can: - View appropriate contact
details. - Call or message each other. - Discuss delays or collection
issues. - Request changes through the app.

The platform should maintain the agreed trip details and record
important changes. Contact information should not be exposed to
unrelated users.

### 16.3 Pickup and delivery verification

Use: - Unique shipment ID. - Optional QR code. - Pickup OTP. - Delivery
OTP. - Timestamped status updates. - Optional photos of cargo/package
count at pickup and delivery.

This helps distinguish booked, picked-up and delivered shipments.

------------------------------------------------------------------------

## 17. Weather and journey-risk intelligence

Investigate India Meteorological Department (IMD) APIs and available
official weather feeds.

Potential information: - Rainfall forecasts. - District warnings. - Heat
conditions. - Thunderstorm warnings. - Strong wind warnings. - Other
relevant alerts.

Potential actions: - Add a transparent estimated journey buffer. - Warn
drivers about weather conditions. - Flag exposed/open vehicles carrying
vulnerable cargo. - Remind drivers about waterproof covering or other
appropriate protection. - Recommend human review of potentially affected
routes.

Do not claim that weather data proves a specific rural road is closed.
Do not automatically route a driver onto an unverified alternative.

Weather should influence risk estimates and alerts, not replace
road-condition verification.

------------------------------------------------------------------------

## 18. Optional hardware: smart weighing and cold-chain monitoring

These are stretch features, not prerequisites for the core prototype.

### 18.1 Smart weighing station

Possible components: - ESP32. - HX711 load-cell amplifier. - Load
cell/platform. - QR code to identify shipment. - Wi-Fi/Bluetooth
connection to the application.

At an FPO collection point, the measured weight can update the
shipment's verified quantity and vehicle capacity.

The readings are prototype logistics measurements, not certified
commercial weighments unless the hardware and calibration meet the
applicable requirements.

### 18.2 Temperature monitoring

For a refrigerated shipment, an optional temperature sensor can report
readings during transit.

The system can: - Record timestamped readings. - Compare readings with
the declared required range. - Flag excursions. - Notify relevant
participants. - Retain a trip record.

For the hackathon, simulated sensor data may be sufficient if a physical
sensor is not feasible. Clearly label simulated readings.

------------------------------------------------------------------------

## 19. Recommended technology stack

The proposed stack balances technical capability and prototype
feasibility.

  -----------------------------------------------------------------------
  Layer                   Proposed technology     Purpose
  ----------------------- ----------------------- -----------------------
  Frontend                React + TypeScript      User interfaces

  Mobile experience       Progressive Web App     Mobile-first access and
                          (PWA)                   offline support

  Backend                 Python + FastAPI        APIs and business logic

  Database                PostgreSQL              Users, shipments,
                                                  vehicles, bookings

  Geospatial database     PostGIS                 Location and geographic
                                                  queries

  Real-time updates       Supabase Realtime or    Trip status/location
                          Firebase                updates

  Optimisation            Google OR-Tools         Vehicle routing and
                                                  allocation

  Maps                    OpenStreetMap + Leaflet Map display

  Routing                 OSRM or another         Road route, distance
                          suitable routing engine and duration

  Voice                   Bhashini / AI4Bharat,   Speech, translation and
                          subject to access       TTS

  AI orchestration        LLM with structured     Conversational
                          tool calling            workflows and tool
                                                  coordination

  Weather                 IMD APIs                Weather-risk
                                                  information

  Optional hardware       ESP32 + sensors         Weighing or cold-chain
                                                  prototype
  -----------------------------------------------------------------------

### Architecture principle

Use AI for: - Natural-language understanding. - Voice conversations. -
Extracting structured fields. - Asking follow-up questions. - Explaining
recommendations. - Coordinating workflow tools.

Use deterministic, testable software for: - Vehicle eligibility. -
Capacity calculation. - Route optimisation. - Time-window validation. -
Price allocation. - Booking state transitions. - Permission checks.

Do not ask an LLM to invent optimal routes, calculate binding commercial
settlements, or override hard cargo-safety constraints.

------------------------------------------------------------------------

## 20. Suggested agent architecture

Use one central orchestrator with modular agents/tools rather than many
independent LLMs.

### Central Orchestrator

Maintains workflow state, delegates tasks, invokes tools and ensures
that user confirmation is obtained before consequential actions.

### Supplier Agent

Collects shipment details, identifies missing fields, manages saved
templates and recurring shipment requests.

### Fleet Agent

Maintains driver/vehicle records, availability, current loads and
capacity.

### Freshness Priority Engine

Calculates urgency and delivery slack from verified or explicitly
uncertain inputs.

### Matching Agent

Filters feasible vehicles, calls the routing/optimisation engine and
ranks options.

### Backhaul Agent

Finds compatible shipments for return journeys and route corridors.

### Scheduling Agent

Creates recurring trip instances, requests driver confirmation and
handles missed confirmations or replacements.

### Journey Agent

Monitors trip milestones, delays, weather alerts, cancellations and
re-optimisation triggers.

### Language/Voice Interface

Handles speech recognition, translation, spoken responses and
confirmation. It can be implemented as a shared interface to the other
agents rather than a separate autonomous decision-maker.

All agents should use shared, permission-controlled records. Avoid
duplicating conflicting versions of shipment or vehicle state.

------------------------------------------------------------------------

## 21. Data sources and external resources to investigate

Potential resources identified for the project:

### Rural road and geographic data

-   PMGSY GeoSadak open data: `https://geosadak-pmgsy.nic.in/opendata`
-   OpenStreetMap: `https://www.openstreetmap.org/`
-   OSRM documentation: `https://project-osrm.org/`

Use multiple sources where appropriate. A mapped road is not a guarantee
that every vehicle can safely use it. Rural road suitability may require
field verification, road-class restrictions and driver feedback.

### Agricultural market information

-   AGMARKNET / data.gov.in: investigate official market price datasets.
-   Use mandi prices as supporting market context only; they are not
    guaranteed buyer quotations or proof that a buyer will purchase the
    shipment.

### Weather

-   India Meteorological Department: investigate current API access,
    data coverage, terms and rate limits.

### Indian language technology

-   Bhashini: investigate API onboarding and supported services.
-   AI4Bharat: investigate IndicConformer and IndicTrans2, including
    current model licences and deployment requirements.

### Optimisation

-   Google OR-Tools: `https://developers.google.com/optimization`
-   CVRPLIB: `http://vrp.galgos.inf.puc-rio.br/`

CVRPLIB can support routing benchmark tests, but it is not a rural
Indian freight dataset. Create project-specific test scenarios as well.

### Important data gap

There is no assumed dependable public dataset for real-time rural tempo
availability, empty capacity, cancellations, return loads and actual
rural freight prices. Collect a small pilot dataset where possible and
create clearly labelled synthetic data for repeatable testing. Never
present synthetic data as field observations.

------------------------------------------------------------------------

## 22. Prototype scope: what to build first

The full vision is broad. The four-person team should protect the core
workflow and avoid adding features before the optimisation works.

### Must-have prototype

1.  Supplier registration and shipment creation.
2.  Transporter registration and vehicle/fleet details.
3.  Dynamic cargo and handling fields.
4.  Voice-assisted shipment intake, with a text/form fallback.
5.  Perishability-aware urgency and delivery-slack assessment.
6.  Vehicle compatibility filtering.
7.  Location and route-aware matching.
8.  Capacity-aware shipment consolidation.
9.  Driver offer: accept, reject and optionally counteroffer.
10. Supplier confirmation and contact sharing.
11. Saved shipment templates.
12. Recurring shipment schedules and driver confirmation.
13. Return-load matching.
14. Map-based route and trip status.
15. Transparent price breakdown.
16. Baseline-versus-optimised performance dashboard.

### Should-have features

-   Kannada voice input/output.
-   Live GPS where supported.
-   Last-updated location timestamp.
-   Weather alerts.
-   Offline request queue and sync.
-   Pickup/delivery OTP.
-   QR shipment identification.
-   Cancellation recovery.
-   Notifications.
-   Coordinator dashboard.

### Stretch features

-   ESP32 weighing station.
-   Temperature sensor integration.
-   More regional languages.
-   Predictive demand models based on collected history.
-   Advanced route uncertainty modelling.
-   Quantum-inspired optimisation experiment.

Do not sacrifice a reliable end-to-end core workflow to build every
stretch feature.

------------------------------------------------------------------------

## 23. Prototype geography and demonstration scenario

Start with one defined rural catchment, a nearby mandi or processing
hub, and a corresponding return corridor.

A Bengaluru--Chennai corridor can be used as an illustrative
long-distance return-load example, but the actual pilot geography should
be selected based on access to suppliers, drivers and realistic route
data.

### Suggested live demo

**Scene 1 --- Independent requests** - Supplier A has 450 kg of tomatoes
in Village A. - Supplier B has 350 kg of tomatoes in Village B. - A
distributor has compatible empty produce crates that need to travel
towards the suppliers' region.

**Scene 2 --- Matching** - GATIQ checks cargo compatibility, weight,
volume, pickup times, delivery deadlines and vehicle availability. - The
optimiser proposes a feasible consolidated route. - The dashboard
displays the pickup sequence, capacity use and cost allocation.

**Scene 3 --- Driver choice** - Driver receives the trip details and
payout. - Driver accepts, rejects or counteroffers. - Supplier reviews
and confirms.

**Scene 4 --- Failure test** - Cancel the selected driver before
pickup. - GATIQ removes that vehicle and re-optimises uncommitted
shipments. - A replacement offer is presented. - Supplier approves any
changed terms.

**Scene 5 --- Return load** - After delivery, the Backhaul Agent finds a
compatible return shipment along the corridor. - Driver reviews and
chooses whether to accept.

**Scene 6 --- Recurring shipment** - Supplier creates a recurring 30 kg
tomato shipment every Monday at 7 AM. - A preferred driver agrees to the
recurring arrangement. - The next trip instance is generated and
confirmation is requested. - If the driver is unavailable, the supplier
is notified and offered alternatives.

**Scene 7 --- Tracking** - Display route, trip milestones, location
update timestamp and delivery confirmation.

The demo should show real system state changes, not just a sequence of
static screens.

------------------------------------------------------------------------

## 24. Evaluation and benchmarking

The proposed system must be compared against a simple baseline using
identical requests, vehicles, routes and constraints.

### Baseline

A nearest-feasible-vehicle approach: - Find the nearest available
vehicle. - Apply basic capacity and eligibility checks. - Assign a
shipment without advanced pooling/backhaul optimisation.

### GATIQ

-   Cargo compatibility.
-   Perishability-aware prioritisation.
-   Multiple pickup/delivery routing.
-   Weight and volume constraints.
-   Time windows.
-   Load consolidation.
-   Return-load matching.
-   Dynamic re-optimisation.

### Metrics

  -----------------------------------------------------------------------
  Metric                              What it measures
  ----------------------------------- -----------------------------------
  Vehicle utilisation                 Used capacity relative to available
                                      capacity

  Empty kilometres                    Distance travelled without cargo

  Cost per shipment                   Estimated freight cost per shipment

  Cost per tonne-km                   Transport cost relative to freight
                                      work

  On-time delivery rate               Deliveries meeting declared
                                      deadlines

  Fulfilment rate                     Requests successfully
                                      assigned/completed

  Cancellation recovery time          Time to find a feasible replacement

  Solver runtime                      Practicality of the optimisation

  Detour                              Additional distance/time due to
                                      pooling

  Cargo-incompatibility rejection     Whether unsafe/infeasible options
                                      are correctly filtered
  -----------------------------------------------------------------------

Use multiple test instances and random seeds. Report median and spread,
not only the best run.

### Rural simulation dataset

Start with: - 20--40 shipment requests. - 5--10 heterogeneous
vehicles. - 10--20 locations. - Different cargo types. - Different
payload and volume capacities. - Multiple pickup/delivery windows. -
Some urgent and flexible shipments. - A mix of available, delayed and
cancelled vehicles. - Outbound and return demand.

Stress-test: 1. Low and high shipment density. 2. Low and high
return-load availability. 3. Sudden driver cancellation. 4. Perishable
cargo with tight deadlines. 5. Incorrectly declared weight. 6. Missing
road links. 7. Poor connectivity. 8. Cargo incompatibility. 9. Delayed
pickup. 10. Supplier destination changes.

Report which data is synthetic and which is collected from actual users.

### Quantum-inspired optimisation

The challenge permits investigation of classical or quantum-inspired
approaches, but quantum hardware is not required. Do not add quantum
terminology merely for novelty.

First build and benchmark a reliable classical OR-Tools implementation.
Only then consider a simulated annealing or QUBO-style experiment if it
produces a measurable benefit on a clearly defined subproblem.

------------------------------------------------------------------------

## 25. Real-world risks and safeguards

  -----------------------------------------------------------------------
  Risk                                Proposed handling
  ----------------------------------- -----------------------------------
  Too few nearby shipments            Maximum pooling wait and
                                      dedicated-trip fallback

  Incorrect weight                    Mark estimated/verified; confirm at
                                      pickup; recalculate capacity

  Cargo too large despite acceptable  Check volume and dimensions
  weight                              

  Incompatible food                   Hard cargo compatibility
                                      constraints

  Unsuitable vehicle                  Reject or flag; never override
                                      safety for urgency

  Incomplete road map                 Combine data sources, apply
                                      restrictions, allow driver
                                      confirmation

  Driver cancellation                 Re-optimise uncommitted shipments

  Supplier changes quantity           Recalculate feasibility, cost and
                                      obtain approval

  Poor GPS connectivity               Show last reported location and
                                      timestamp

  Voice recognition error             Read back fields and request
                                      confirmation

  Low digital literacy                Voice-first flow and assisted
                                      coordinator booking

  No historical data                  Rule-based cold start and clearly
                                      labelled synthetic tests

  Weather disruption                  Risk warning and human review, not
                                      invented road closure

  Dispute over price                  Explainable allocation and recorded
                                      accepted quote

  No return load                      Respect driver's departure window;
                                      allow empty return

  Duplicate recurring booking         Separate schedule from each
                                      generated shipment instance

  Driver does not confirm recurrence  Notify supplier and seek
                                      replacement approval

  Privacy concern                     Consent-based location sharing and
                                      role-based contact visibility
  -----------------------------------------------------------------------

### Explicit non-goals for the first prototype

-   No claim of guaranteed food preservation.
-   No automatic assignment that forces drivers to accept.
-   No guaranteed driver attendance for recurring bookings.
-   No automatic payment/escrow requirement.
-   No insurance underwriting.
-   No blockchain requirement.
-   No claim that a weather warning confirms a road closure.
-   No claim of continuous GPS when the device is offline or background
    tracking is unavailable.
-   No certification of food safety or commercial weighing unless the
    relevant standards are actually met.

------------------------------------------------------------------------

## 26. Business and adoption model

The marketplace has a chicken-and-egg problem: suppliers need available
vehicles, and transporters need enough shipments.

Start with an anchor organisation: - FPO. - Mandi operator. - Produce
aggregator. - Rural business cluster. - Local transporter association.

This organisation can help bring both demand and vehicle supply into the
network.

Potential revenue streams to validate: 1. Subscription for
FPOs/aggregators using dispatch and coordination tools. 2. Optional fee
per successfully completed matched trip. 3. Premium analytics and fleet
coordination for larger rural businesses.

Initial priority should be FPOs and aggregators rather than charging
individual small farmers. Pricing and willingness to pay must be
validated through interviews.

------------------------------------------------------------------------

## 27. Four-person team responsibilities

Suggested workstreams:

### Person 1 --- AI and optimisation

-   OR-Tools implementation.
-   Candidate generation.
-   Capacity/time-window constraints.
-   Perishability priority.
-   Consolidation and backhaul.
-   Cancellation re-optimisation.
-   Benchmarking with Person 4.

### Person 2 --- Backend and data

-   FastAPI.
-   PostgreSQL/PostGIS.
-   User, vehicle, shipment and booking models.
-   API contracts.
-   Routing matrix integration.
-   Price allocation.
-   Recurring schedule and trip-instance logic.

### Person 3 --- Frontend and user experience

-   React/TypeScript PWA.
-   Supplier, driver and coordinator interfaces.
-   Shipment forms and saved templates.
-   Voice interaction interface.
-   Map and trip status.
-   Offline request experience.

### Person 4 --- AI integration and validation

-   Voice and language integration.
-   LLM structured extraction and tool orchestration.
-   Weather integration.
-   Test-data generation and field research.
-   Failure testing and demo validation.
-   Benchmark presentation and pitch.

The workstreams must integrate continuously. Person 1 and Person 2
should agree on shared data structures early. The frontend should call
real APIs as soon as the first backend endpoints exist.

------------------------------------------------------------------------

## 28. Five-week development roadmap

This is a proposed sequence, not a claim about the current official
competition deadline.

### Week 1 --- Validation and foundation

-   Interview suppliers, drivers and FPO/aggregator representatives.
-   Select a pilot catchment and return corridor.
-   Define shipment, vehicle, driver, booking and schedule schemas.
-   Obtain/inspect road data.
-   Build a nearest-feasible-vehicle baseline.

**Milestone:** Validated workflow and working data model.

### Week 2 --- Platform foundation

-   Implement registration.
-   Build shipment and vehicle forms.
-   Create core APIs and database.
-   Integrate map and route matrix.
-   Seed realistic test data.

**Milestone:** End-to-end booking workflow.

### Week 3 --- Optimisation

-   Implement eligibility filtering.
-   Add capacity and time-window constraints.
-   Implement shipment consolidation.
-   Add return-load matching.
-   Add cost allocation.
-   Compare against baseline.

**Milestone:** Working optimisation engine.

### Week 4 --- Agentic and operational features

-   Integrate voice intake and read-back.
-   Implement saved templates and recurring schedules.
-   Add driver offers and confirmation.
-   Add trip status and location.
-   Implement cancellation recovery.
-   Add weather alerts and offline fallback where feasible.

**Milestone:** Complete differentiated workflow.

### Week 5 --- Validation and presentation

-   Run benchmark and stress tests.
-   Validate with real users if possible.
-   Fix critical bugs.
-   Record measured metrics.
-   Prepare demo, architecture diagram and pitch.
-   Prepare a reliable offline/demo fallback.

**Milestone:** Competition-ready prototype.

------------------------------------------------------------------------

## 29. Presentation structure

A concise 8-slide pitch is recommended.

### Slide 1 --- GATIQ

**An Agentic AI-Powered Rural Food Freight Network**

Connecting food suppliers with the right transport, reducing empty
journeys and preventing avoidable food loss.

### Slide 2 --- The Problem

-   Small suppliers struggle to find suitable and affordable transport.
-   Vehicles travel partially loaded or return empty.
-   Perishable food loses value when transport is delayed.
-   Local drivers face language and digital literacy barriers.
-   Repeated shipments require repeated coordination.

### Slide 3 --- Our Solution

A two-sided platform that connects suppliers and transport providers
through cargo-aware matching, load consolidation, driver-controlled trip
offers and return-load optimisation.

### Slide 4 --- How It Works

Register → Voice/form shipment intake → Intelligent matching → Driver
accepts → Supplier confirms → Track delivery → Find next/return load.

### Slide 5 --- The Intelligence

Supplier/voice agent, fleet agent, freshness priority engine,
matching/optimisation engine, backhaul agent, scheduling agent and
journey agent.

### Slide 6 --- What Makes It Different

-   Voice-first regional-language access.
-   Perishability-aware transport priority.
-   Saved shipment templates and recurring driver arrangements.
-   Dynamic load consolidation.
-   Return-load matching.
-   Transparent driver offers and cost allocation.

### Slide 7 --- Technology

React/TypeScript PWA, Python/FastAPI, PostgreSQL/PostGIS, LLM tool
calling, Bhashini/AI4Bharat, OR-Tools, OpenStreetMap/OSRM, GPS and IMD.

### Slide 8 --- Impact and Validation

Show the pilot geography, baseline comparison, vehicle utilisation,
empty kilometres, cost per shipment, on-time delivery and cancellation
recovery. End with:

**Turn fragmented shipments into connected journeys, and empty miles
into productive movement.**

Do not present unmeasured savings as achieved results. Label projections
and synthetic-demo metrics clearly.

------------------------------------------------------------------------

## 30. Product principles --- decisions that should not change casually

1.  GATIQ is a freight coordination and optimisation network, not merely
    a truck listing app.
2.  Supplier and transporter both retain control over commercial
    commitments.
3.  Drivers voluntarily accept, reject or counteroffer trips.
4.  Cargo suitability is a hard constraint; urgency cannot override it.
5.  Weight and volume must both be considered.
6.  Capacity must be tracked across route segments, not only at trip
    start.
7.  Perishability priority must use available product/condition/time
    information and expose uncertainty.
8.  Voice-first regional-language interaction is a core accessibility
    requirement.
9.  Voice-derived information must be read back and confirmed.
10. Saved templates, recurring schedules and individual trip instances
    are separate concepts.
11. A recurring schedule is not a guarantee of driver attendance; each
    occurrence needs availability/confirmation and a recovery path.
12. Return-load matching is a core capability.
13. Location sharing requires consent and must show data freshness.
14. LLMs interpret and coordinate; deterministic code enforces
    constraints and calculates routes/prices.
15. Synthetic data must never be represented as real field data.
16. Benchmark against a simple baseline using identical scenarios.
17. Build the core optimisation workflow before stretch features.
18. Do not promise zero spoilage, zero empty journeys or guaranteed
    savings.

------------------------------------------------------------------------

## 31. Instructions for an AI assistant working on GATIQ

When helping the team, use the following context and rules.

### Understand the project

GATIQ is an agentic-AI-assisted rural food freight network for
Tech4Bharat Problem Statement 5.3. Its central technical value is
perishability-aware, cargo-compatible vehicle matching, shipment
consolidation and return-load optimisation, supported by voice-first
access and recurring logistics workflows.

### Preserve the key decisions

Do not casually remove: - Supplier and transporter roles. - Fleet and
individual vehicle distinction. - Food category and handling
requirements. - Voice-based conversational intake for suppliers and
drivers. - Structured shipment tables generated from confirmed
conversation details. - Saved shipment templates. - Recurring shipment
schedules with driver confirmation. - Freshness/perishability
prioritisation. - Hard cargo compatibility and capacity constraints. -
Driver-controlled accept/reject/counteroffer. - Mutual booking
confirmation before sharing contact details. - Return-load matching. -
Map-based trip information and consent-based tracking. - Weather-risk
information. - Baseline benchmarking.

### Be technically honest

-   Never invent APIs, datasets, model performance, market prices or
    field research.
-   Check current documentation before relying on external APIs or
    services.
-   Verify API keys, quotas, licensing, data access and deployment
    requirements.
-   Clearly distinguish real data, manually entered data, simulated data
    and model estimates.
-   Do not call a simulated GPS trace "live tracking."
-   Do not call an estimated cargo weight "verified."
-   Do not call an account "verified" without a real verification
    process.
-   Do not claim food safety, shelf-life or temperature compliance
    without appropriate validated rules and evidence.
-   Never let an LLM override hard capacity, route, timing or
    cargo-safety constraints.

### When writing code

-   Prefer modular, testable components.
-   Define shared schemas and API contracts before parallel
    implementation.
-   Use explicit shipment, vehicle, driver, trip, offer, recurring
    schedule and trip-instance states.
-   Keep booking and payment-related state transitions auditable.
-   Add validation and error handling for missing, uncertain or
    conflicting user input.
-   Include tests for overcapacity, incompatible cargo, time-window
    violations, cancellation, stale GPS and duplicate recurring
    instances.
-   Make the prototype usable with seeded demo data if external services
    are unavailable.
-   Keep the core workflow operational without optional integrations.

### When making product decisions

Prioritise: 1. Safety and feasibility. 2. Reliable end-to-end workflow.
3. Measurable optimisation. 4. User accessibility. 5. Driver and
supplier trust. 6. Prototype feasibility. 7. Optional novelty features.

If a proposed feature increases complexity without improving the core
problem or measurable outcome, recommend postponing it.

### Expected response style

Give practical, implementation-ready advice. Explain trade-offs.
Separate must-have from stretch scope. When proposing an algorithm,
state its inputs, constraints, outputs and evaluation method. When
proposing a feature, explain the user flow, data required, failure cases
and how it fits the existing architecture.

------------------------------------------------------------------------

## 32. One-paragraph project summary

GATIQ is a multilingual, agentic-AI-powered rural food freight network
that connects food suppliers with suitable transport providers.
Suppliers and drivers can create shipment and vehicle records through
forms or conversational voice interactions, with the AI asking follow-up
questions and converting confirmed responses into structured data. A
freshness-priority engine evaluates perishability and delivery slack,
while a deterministic optimisation engine checks cargo compatibility,
weight, volume, location, time windows and route feasibility to
recommend vehicles and consolidate shipments. Drivers retain control
through accept, reject and counteroffer workflows, and suppliers receive
trip details and contact access after mutual confirmation. GATIQ also
supports saved shipment templates, recurring bookings with driver
confirmation, map-based journey updates, weather-risk information,
dynamic capacity tracking, cancellation recovery and return-load
matching. Its performance is evaluated against a
nearest-feasible-vehicle baseline using vehicle utilisation, empty
kilometres, cost, on-time delivery, fulfilment and recovery time.

------------------------------------------------------------------------

**End of README --- GATIQ Project Context Pack**

This document records the current project direction and proposed
prototype. Treat implementation details and external integrations as
proposals until tested and confirmed by the team.
