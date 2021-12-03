## Introduction

**Product Data** is a collection of objects defining **dry** products. Any transaction request may have zero or more products. Not to be confused with fuel values.

## Data Structure

| Field Name          | Size | Type            | Condition   | Descriptions/Field Value(s)                                                        |
| ------------------- | ---- | --------------- | ----------- | ---------------------------------------------------------------------------------- |
| ServiceCode         | Var  | string          | Optional    |                                                                                    |
| ProductCode         | Var  | string          | Required    | Dry product code                                                                   |
| ProductUnitPrice    | Var  | decimal         | Conditional | Required if the *ProductCode* is not configured in the host                        |
| ProductNetUnitPrice | Var  | decimal         | Optional    |                                                                                    |
| ProductAmount       | Var  | decimal         | Conditional | Required if the *ProductCode* is not configured in the host                        |
| ProductNetAmount    | Var  | decimal         | Optional    |                                                                                    |
| ProductQuantity     | Var  | decimal         | Required    | 1 - 999                                                                            |
| UnitCode            | Var  | string          | Optional    | Refer to [Measurement Unit Codes Annex](./AN-Native-MeasurementUnitCodes-Annex.md) |
| ProductTaxes        | Var  | List[AuthTaxes] | Optional    | Refer to [Auth Taxes Annex](./AN-Native-MeasurementUnitCodes-Annex.md)             |