\# System Design Specification

\*\*Course:\*\* AI Project Design and Development (AI-316)  

\*\*Lab 02:\*\* System Requirements \& Software Architecture



\---



\## Task 1: Functional \& Non-Functional Requirements Breakdown

\*\*System:\*\* Smart Automated Attendance System



\### Functional Requirements



| ID | Requirement Description |

|---|---|

| FR-01 | The system must capture video feeds and perform real-time face detection. |

| FR-02 | The system must extract facial embeddings and match them against the registered employee database. |

| FR-03 | Upon successful recognition, the system must log the timestamp, user ID, and match confidence. |

| FR-04 | The system must provide immediate visual feedback (success/failure) on an edge display. |

| FR-05 | The system must synchronize offline attendance logs with the central cloud database when network connectivity is restored. |



\### Non-Functional Requirements



| ID | Requirement Description |

|---|---|

| NFR-01 | \*\*Performance:\*\* The system must maintain a minimum processing speed of 15 frames per second (FPS). |

| NFR-02 | \*\*Accuracy:\*\* The facial recognition model must achieve a precision threshold of >98% to prevent false positives. |

| NFR-03 | \*\*Efficiency:\*\* Edge device power consumption must remain below 15W during peak inference load. |

| NFR-04 | \*\*Security/Privacy:\*\* Facial embeddings must be encrypted at rest (AES-256) and never stored as raw images. |

| NFR-05 | \*\*Reliability:\*\* The system must automatically recover and resume logging within 30 seconds of a power cycle. |



\---



\## Task 2: System Boundary \& Input/Output Mapping

\*\*System:\*\* AI-Powered Surveillance Application



\### System Actors



\* \*\*Security Operator:\*\* Monitors the dashboard for anomalies and reviews alerts.

\* \*\*Admin:\*\* Configures model thresholds, adds cameras, and manages user access.

\* \*\*Automated Trigger System:\*\* Physical alarm bells or automated security gates.



\### Input/Output \& Boundary Specification



| Category | Details |

|---|---|

| \*\*System Inputs\*\* | RTSP Video Streams (1080p, 30fps), Motion Sensor Interrupts, Admin Configuration Parameters. |

| \*\*System Outputs\*\* | Bounding box coordinates (JSON), Alert notifications (Email/SMS), Database log entries. |

| \*\*Operational Constraints\*\* | Maximum memory footprint < 4GB on edge nodes; Bandwidth usage limited to 5Mbps per camera. |



\---



\## Task 3: Data-Flow Diagram (DFD)



\### Level 0: Context Diagram



```mermaid

graph TD

&#x20;   Camera\[Camera / Sensor] -->|Raw Video Stream| System\[AI Object Detection System]

&#x20;   System -->|Alerts \& Analytics| Operator\[Security Operator]

&#x20;   System -->|Detection Logs| DB\[(Central Database)]
