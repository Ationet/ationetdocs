## Introduction

**Auth Taxes** is an object defining taxes. Any transaction request or dry product may have zero or more taxes.

## Data Structure

| Field Name  | Size | Type    | Condition   | Descriptions/Field Value(s)                                                        |
| ----------- | ---- | ------- | ----------- | ---------------------------------------------------------------------------------- |
| Code        | Var  | string  | Optional    |                                                                                    |
| Description | Var  | string  | Required    | Dry product code                                                                   |
| Factor      | Var  | decimal | Conditional | Required if the *ProductCode* is not configured in the host                        |
| Amount      | Var  | decimal | Optional    |                                                                                    |
| Value       | Var  | decimal | Conditional | Required if the *ProductCode* is not configured in the host                        |
| FactorValue | Var  | decimal | Optional    |                                                                                    |
| Base        | Var  | decimal | Required    | 1 - 999                                                                            |
| Included    | Var  | string  | Optional    | Refer to [Measurement Unit Codes Annex](./AN-Native-MeasurementUnitCodes-Annex.md) |



public string Code { get; set; }
    public string Description { get; set; }
    public string Factor { get; set; }
    public decimal? Amount { get; set; }
    public decimal? Value { get; set; }
    public decimal? FactorValue { get; set; }
    public decimal? Base { get; set; }
    public bool? Included { get; set; }