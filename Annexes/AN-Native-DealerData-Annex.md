## Introduction

**Dealer Data** is a field of type `Dictonary<string, string>` meaning that every element in the collection has a **Key** and **Value**. The contents of this field vary according to the different business rules that are configured within the host. Only used in a request message, will not be present in a host response.

Being a dictonary data type means that you may send any key/value combination and the host will take it as valid. However, only certain keys are taken into account in a request message.

## Keys

| Key           | Description                                                      |
| ------------- | ---------------------------------------------------------------- |
| AttendantCode | *Attendant* code responsible for the *Transaction* in the *Site* |
| PumpSide      | The side of the *Pump* which the *Transaction* was made in       |