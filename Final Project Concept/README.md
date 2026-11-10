# Count My Shots

## Final Project Concept — Interactive Device Design

**Author:** Ziji Zhang  
**Status:** Concept proposal; implementation and evaluation are planned.

> Count My Shots combines a hoop-mounted sensor with a courtside camera to record basketball shooting practice automatically. Players shoot normally while the system tracks attempts, made baskets, and shooting percentage.

## Motivation

During solo basketball practice, keeping track of attempts and made baskets adds a task alongside shooting and retrieving the ball. Losing count makes it harder to understand how a session went or compare it with another session. Recording video can help, but reviewing a long recording to find individual shots also takes effort.

I want to build a device that fits the way people already practice basketball. The player should not need to press a button after every shot, respond to spoken prompts, or follow an additional game. The basketball activity itself provides the input.

The design question is:

**How can an interactive system provide useful, trustworthy shooting records while allowing a player to practice without interruption?**

## Concept Overview

The system has four main components:

1. A fixed courtside camera observes the player and identifies shot attempts.
2. A sensor assembly near the hoop detects the ball passing downward through the basket.
3. A processing system matches these events and maintains the session record.
4. A courtside display shows progress and provides a review interface after practice.

The camera and hoop sensor have complementary roles. The camera helps establish when a shot was attempted, while the hoop sensor provides evidence that a basket was made. Combining them may produce a more useful record than either input alone, but this must be tested rather than assumed.

## Intended User and Setting

The initial user is a recreational basketball player practicing alone at one basket. The first prototype will support a fixed shooting area, beginning with free throws, and one stationary camera with a clear view of the player and hoop.

The player retrieves the ball normally between attempts. Other players, simultaneous shots, and changing camera positions are outside the first prototype's scope.

A mini hoop and soft ball can support initial classroom testing of sensing, event matching, and display behavior. Performance on a mini hoop will not be treated as evidence that the same setup works on a full-size court. Real-court operation requires separate validation.

## User Experience

### Before Practice

The player positions the camera, checks the visible connection and sensing status, and selects a session goal, such as 30 attempts. A short setup view helps confirm that the shooting area is visible. The player presses Start once and begins practicing.

### During Practice

The player shoots, retrieves the ball, and shoots again. The system observes this activity and updates the display after each result is resolved. Feedback is primarily visual and does not require acknowledgment.

An example display, when all recorded attempts have resolved outcomes, is:

| Attempts | Made | Shooting Percentage |
| ---: | ---: | ---: |
| 20 | 12 | 60% |

If a result is uncertain, the display shows a pending-review count and marks the percentage as provisional. It should not present unresolved data as a final statistic.

Reaching the goal produces a brief completion cue. The player can then end the session or continue practicing; the system should not silently discard additional shots.

### After Practice

The player presses End and reviews the session summary. A timeline lists recorded attempts, their outcomes, and any events requiring confirmation. Short video clips help the player inspect ambiguous records and correct mistakes.

The final record contains total attempts, made baskets, missed baskets, shooting percentage, and any remaining unresolved events. Corrections update the statistics and remain distinguishable from automatic decisions.

## Storyboard

| Frame | Player Action | System Response |
| --- | --- | --- |
| 1. Set up | Places the camera, checks readiness, and chooses a target | Shows camera framing, sensor status, and session settings |
| 2. Begin | Presses Start and walks to the shooting position | Starts a session and displays zero recorded attempts |
| 3. Shoot | Takes a normal shot | Detects a candidate attempt and waits for outcome evidence |
| 4. Score | The ball passes through the basket | Matches the hoop event to the attempt and updates the score |
| 5. Continue | Retrieves the ball and takes another shot | Records the next event without requiring another button press |
| 6. Review | Ends practice and checks the summary | Shows statistics, clips, and any records needing correction |

## Sensing Approach

### Camera: Detecting Attempts

The camera's primary task is to identify shot attempts and assign timestamps. The proposed approach is to examine a sequence of frames for evidence of a shooting action and, where visible, ball release. A single raised-arm pose is not sufficient to establish an attempt.

The prototype must distinguish shooting from movements such as dribbling, retrieving the ball, passing, and pump fakes. Restricting the first version to one player and one shooting area makes these cases easier to investigate.

The specific vision model, processing resolution, and frame rate will be selected after testing recorded footage. No particular accuracy or real-time performance is assumed at the concept stage.

### Hoop Sensor: Detecting Made Baskets

The hoop assembly will detect the ball moving downward through the basket. One candidate design uses two vertically separated optical sensing zones: an upper trigger followed by a lower trigger could provide evidence of downward passage.

This arrangement is a hypothesis to prototype, not a finalized hardware design. Coverage across the basket opening, ball speed, net movement, ambient light, and physical mounting all need investigation. A narrow beam may miss a ball passing elsewhere through the opening, while movement of the net may cause false triggers.

A vibration sensor alone would not reliably distinguish a rim impact from a made basket, so impacts should not automatically count as scores.

The assembly must avoid obstructing the ball or changing normal basket behavior. Any installation must be securely mounted and permitted at the test location.

### Why Use Both?

| Input | Useful Evidence | Limitation |
| --- | --- | --- |
| Camera | A candidate shot attempt and its timing | May miss releases or confuse other movements with shots |
| Hoop sensor | A candidate ball passage through the basket | Cannot independently count all missed attempts |
| Combined record | A relationship between an attempt and an outcome | Depends on reliable timing, detection, and matching |

## Event Matching and Uncertainty

Each detected attempt creates a record containing its timestamp, available video, and a pending outcome. Hoop events are matched to plausible preceding attempts using event order and a calibrated time window.

The matching window will be determined from observed shots rather than an arbitrary universal delay. Communication delays and timestamp alignment must also be considered. A shared clock is preferred; separate devices require measured clock alignment.

The proposed outcome categories are:

- **Made:** a valid hoop event is matched to an attempt.
- **Inferred miss:** no hoop event arrives within the expected window, and the available detection and connection status support completing the record.
- **Needs review:** evidence is ambiguous, a device was unavailable, or multiple events cannot be matched confidently.

An inferred miss remains an inference. A sensor can miss a real basket even while reporting that it is connected. Video review and comparison with manually labeled sessions are therefore important parts of validation.

An unmatched hoop event should be retained for review because it could indicate that the camera missed an attempt. Repeated sensor triggers from one basket should be grouped into one passage event rather than counted as multiple makes.

For a fully resolved session:

**Shooting percentage = made baskets / total attempts × 100.**

For zero attempts, the display shows a dash instead of a percentage. When outcomes are unresolved, the display shows confirmed makes, recorded attempts, and the unresolved count, with any percentage explicitly labeled provisional. Users can also add a missed attempt or remove a false attempt during review.

## Interaction and Physical Design

The courtside display should use large, readable numbers. The player should be able to glance at progress without approaching a small screen after every shot. A larger external display may therefore be appropriate for testing, while a small Raspberry Pi screen can support setup and nearby review.

Controls are concentrated at natural boundaries: Start and goal selection before practice, End and review afterward. An optional sound can acknowledge completion of a goal, but constant speech or per-shot announcements are not required.

The camera, display, power supply, and cables should sit outside the player's movement and ball-retrieval paths. The hoop attachment should be compact and removable. Early prototypes will test sensing and placement before a finished enclosure is designed.

## Proposed Hardware and Software

| Component | Proposed Role |
| --- | --- |
| Raspberry Pi | Receive sensor events, maintain session state, and drive the interface |
| Fixed camera | Capture footage for attempt detection and review |
| Hoop sensor assembly | Detect candidate downward ball passages |
| Optional microcontroller | Read hoop sensors and timestamp events near the basket |
| Courtside display | Show live progress and session summaries |
| Physical controls or touch interface | Start, end, configure, and review sessions |
| Laptop, if needed | Run vision processing during development if the Pi is insufficient |

Software responsibilities include video capture, attempt detection, sensor event filtering, timestamp alignment, event matching, persistent session records, and the display interface.

If the hoop unit and processing device are separate, messaging can build on the distributed interaction explored in Lab 6. Messages should include event identifiers and timestamps so retries do not create duplicate scores.

## Prototype Scope

### Stage 1: Automatic Made-Basket Counter

Build and test the hoop sensor and a visible count. Set a target number of made baskets and update progress automatically.

This stage is independently useful, but it does not claim to calculate shooting percentage because missed attempts are not yet counted.

### Stage 2: Camera-Based Attempt Detection

Record fixed-position shooting sessions and manually label actual attempts. Develop the attempt detector against footage containing both shots and confusing non-shot movements.

Test attempt detection independently before combining it with the hoop sensor.

### Stage 3: Integrated Shooting Record

Combine attempt and hoop events, update live statistics, save short clips, and support post-session corrections. Demonstrate the complete experience from setup through review.

### Outside the Initial Scope

- Multiple players or simultaneous balls.
- Full-game scoring and player identification.
- Automatic two-point versus three-point classification.
- Biomechanical assessment or injury-related recommendations.
- Automatic ball retrieval.
- Claims of improved shooting performance.

## Evaluation Plan

Evaluation will examine both sensing performance and the experience of using the device. An observer will manually label attempts and outcomes to create a reference record.

| Area | Evaluation Question |
| --- | --- |
| Attempt detection | How many real attempts are detected, and how many non-shot actions are incorrectly counted? |
| Basket detection | How many made baskets are detected, and how often do net movement or impacts create false scores? |
| Event matching | How often is a detected basket assigned to the correct attempt? |
| Update latency | How long after an event does the display show a usable result? |
| Uncertainty | Are ambiguous events identified clearly, and are apparently confident errors also measured? |
| Review | Can players find and correct an inaccurate record without searching through a full recording? |
| Natural use | Can players complete practice without unnecessary stops to operate the device? |

Test footage should include made shots, misses, rim and backboard contacts, pump fakes, dribbling, retrieval, temporary occlusion, and interrupted sensor communication. Sessions used for final evaluation should be separate from those used to tune thresholds.

I will report counts of false detections and missed events alongside accuracy measures, session length, and test conditions. A successful staged demonstration alone will not establish reliability.

## Recording and User Control

The prototype will record only agreed practice sessions. A visible indicator will show when capture is active, and the player will be able to end recording and delete session clips. The intended default is local processing and storage; any later use of a cloud service would require an explicit change to that plan.

Testing should frame the intended player and basket while avoiding unnecessary recording of other court users.

## Connection to Previous Labs

| Lab | Relevant Experience |
| --- | --- |
| [Lab 1](../Lab%201/README.md) | Designing clear feedback and response timing |
| [Lab 2](../Lab%202/README.md) | Raspberry Pi displays, physical controls, and progress visualization |
| [Lab 3](../Lab%203/README.md) | Separating understandable system status from expressive feedback |
| [Lab 4](../Lab%204/README.md) | Physical sensing, mounting, and iterative hardware prototyping |
| [Lab 5](../Lab%205/README.md) | Camera-based observation and records grounded in captured evidence |
| [Lab 6](../Lab%206/README.md) | Communication between devices and a shared application state |

## Questions for In-Class Feedback

- What sensor arrangement is practical to mount near the basket without affecting play?
- Is a fixed-position free-throw session an appropriate first scope?
- What camera view best supports attempt detection and useful video review?
- How should uncertain outcomes appear without distracting the player?
- What evidence would demonstrate sufficient reliability for a final prototype?

## Intended Outcome

Count My Shots should let a player begin a session, practice normally, and finish with a useful record of what happened. Its central interaction is simple: shooting provides the input, sensing creates the record, and the display makes that record available without requiring a separate action after every attempt.

## AI Assistance Disclosure

OpenAI ChatGPT assisted with brainstorming, refining the project scope, and drafting this concept README. The proposed hardware, software, and evaluation have not yet been implemented or validated as part of this project.
