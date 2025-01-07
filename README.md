# Healthcare---db--project-
ERD and SQL script for healthcare system 
CREATE TABLE patient_data (
    patient_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    dob DATE,
    contact_info VARCHAR(100)
);

CREATE TABLE visit_record (
    visit_id INT PRIMARY KEY,
    patient_id INT,
    visit_date DATE,
    reason_for_visit VARCHAR(100),
    FOREIGN KEY (patient_id) REFERENCES patient_data(patient_id)
);

CREATE TABLE treatment_record (
    treatment_id INT PRIMARY KEY,
    visit_id INT,
    treatment_type VARCHAR(100),
    treatment_date DATE,
    FOREIGN KEY (visit_id) REFERENCES visit_record(visit_id)
);

CREATE TABLE laboratory_test (
    test_id INT PRIMARY KEY,
    visit_id INT,
    test_name VARCHAR(100),
    test_result VARCHAR(100),
    test_date DATE,
    FOREIGN KEY (visit_id) REFERENCES visit_record(visit_id)
);

CREATE TABLE supply_chain (
    supply_id INT PRIMARY KEY,
    supply_name VARCHAR(100),
    quantity_in_stock INT
);

CREATE TABLE resource (
    resource_id INT PRIMARY KEY,
    resource_type VARCHAR(100),
    quantity_available INT
);

CREATE TABLE user_role (
    role_id INT PRIMARY KEY,
    role_name VARCHAR(50),
    permissions VARCHAR(200)
);
