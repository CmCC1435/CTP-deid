# Metadata De-identification Manual

## Introduction
The DICOM metadata de-identification process in CHoRUS is performed in two steps:

### Step 1: De-identificaiton Using Pydicom Script
- PatientID and AccessionNumber in teh DICOM metadata are replaced by person_id and image_occurrence_id from the OMOP table.
- Selected data tags (Table 1) are shifted by a predefined number of days (specific to each PatientID)

Table 1. Date tags to be shifted
| Group  | Element | Tag_name  | 
| ------ | ------- | --------- |
| 0008  | 0012  | Instnce Createion Date  |
| 0008  | 0020  | Study Date  |
| 0008  | 0021  | Series Date |
| 0008  | 0022  | Acquisition Date  |
| 0008  | 0023  | Content Date  |
| 0008  | 002a  | Acquisition Date time  |
| 0010  | 0030  | Patient Birth Date  |
| 0018 | 1012  | Date of Secondary Capture |
| 0018 | 1078  | Radio pharmaceutical Start Date Time |
| 0018 | 1079  | Radio pharmaceutical Stop Date Time |
| 0018 | 1200  | Date of Last Calibration |
| 0018 | 700c  | Date of Last Detector Calibration |
| 0032 | 1000  | Scheduled Study Start Date |
| 0032 | 1010  | Scheduled Study Stop Date |
| 0032 | 1040  | Study Arrival Date |
| 0032 | 1050  | Study Completion Date |
| 0038 | 0020  | Admitting Date |
| 0038 | 0030  | Discharge Date |
| 3006 | 0008  | Structure Set Date |

### Step 2: De-identification Using RSNA CTP software
- Remaining DICOM metadata is de-identified using the RSNA CTP software
- Pre-identifeid tags (PatientID, AccessionNumber, selected date tags in Table 1) from Step 1 are preserved
