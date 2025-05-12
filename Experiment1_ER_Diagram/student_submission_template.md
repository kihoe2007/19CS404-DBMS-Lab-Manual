# ER Diagram Submission - Student Name

## Scenario Chosen:
University / Hospital (choose one)

## ER Diagram:
![Screenshot 2025-05-12 101744](https://github.com/user-attachments/assets/57741ef8-de51-41a3-8205-93ae3583ef00)


## Entities and Attributes:
```
Doctor:

Attributes: Doctor-ID, Name, Phone, Address, Specialization

Patient

Attributes: Patient-ID, Name, Gender, Date of Birth, Phone, Address, Insurance Details

Department

Attributes: Department-ID, Department Name, Department Head (Name)

Appointment

Attributes: Appointment-ID, Appointment Date & Time, Reason for Visit

Relationships: Linked to both Doctor-ID and Patient-ID

Medical Record

Attributes: Record-ID, Prescribed Medicines, Medical Instructor
```


## Relationships and Constraints:
```
Assigned ID

Doctor → Department

Cardinality: Many doctors belong to one department

Participation: Total for Doctor (each doctor must belong to a department)

Schedule

Doctor ↔ Patient via Appointment

Cardinality: Many-to-Many

Participation: Partial (not every doctor or patient must have an appointment)

Has Records

Patient ↔ Medical Record

Cardinality: One patient may have many medical records

Participation: Optional, depending on treatment history
```

## Extension (Prerequisite / Billing):
```
To extend this model for billing, we could introduce a Billing entity with attributes such as:

Bill-ID, Amount, Payment Status, Payment Method, Date

Related to: Patient and possibly Appointment for service-based billing
```

## Design Choices:
Focused Scope: Chose key entities directly involved in patient care and hospital operations.

Department Linkage: Doctors are logically grouped into departments, allowing for administrative tracking.

Data Integrity: All relationships reflect realistic, real-world constraints—such as appointments requiring both a doctor and a patient.

Privacy & Structure: Medical records are separately tracked for better security and historical review.
