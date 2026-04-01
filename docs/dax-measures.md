# 📐 DAX Measures

This file contains the core DAX measures used in the **Inventory Intelligence Dashboard**.

## 1. Total Inventory Value
Calculates the total inventory value across On-Hand, Work-in-Progress (WIP), and In-Transit inventory.

```DAX
Total Inventory Value =
SUM('FactInventory'[Shelf Stock ($)]) +
SUM('FactInventory'[WIP ($)]) +
SUM('FactInventory'[GIT ($)])
```

## 2. Total Inventory Quantity
Calculates the total inventory quantity across On-Hand, WIP, and In-Transit inventory.

Total Inventory Quantity =
SUM('FactInventory'[Shelf Stock]) +
SUM('FactInventory'[WIP]) +
SUM('FactInventory'[GIT])

## 3. On-Hand Inventory Value
Returns the value of on-hand inventory only.

On-Hand Inventory Value =
SUM('FactInventory'[Shelf Stock ($)])

## 4. Work-in-Progress Value
Returns the value of work-in-progress inventory only.

WIP Value =
SUM('FactInventory'[WIP ($)])

## 5. In-Transit Inventory Value
Returns the value of in-transit inventory only.

In-Transit Inventory Value =
SUM('FactInventory'[GIT ($)])

## 6. Average Days on Hand
Returns the average Days on Hand (DOH) across the filtered dataset.

Average DOH =
AVERAGE('FactInventory'[DOH])

## 7. On-Hand %
Shows the share of on-hand inventory value as a percentage of total inventory value.

On-Hand % =
DIVIDE([On-Hand Inventory Value], [Total Inventory Value], 0)

## 8. WIP %
Shows the share of WIP inventory value as a percentage of total inventory value.

WIP % =
DIVIDE([WIP Value], [Total Inventory Value], 0)

## 9. In-Transit %
Shows the share of in-transit inventory value as a percentage of total inventory value.

In-Transit % =
DIVIDE([In-Transit Inventory Value], [Total Inventory Value], 0)

## 10. High DOH Count
Counts materials with Days on Hand above the defined threshold.

High DOH Count =
CALCULATE(
    COUNTROWS('FactInventory'),
    'FactInventory'[DOH] > 45
)

## 11. Low Safety Stock Count
Counts rows where on-hand inventory is below safety stock.

Low Safety Stock Count =
CALCULATE(
    COUNTROWS('FactInventory'),
    'FactInventory'[Shelf Stock] < 'FactInventory'[Safety Stock]
)

## 12. Selected Inventory Value
Dynamic measure used with the Inventory Type selector to switch between On-Hand, WIP, In-Transit, and Total inventory value.

Selected Inventory Value =
SWITCH(
    SELECTEDVALUE('DimInventoryType'[Inventory Type], "Total"),
    "On-Hand", [On-Hand Inventory Value],
    "WIP", [WIP Value],
    "In-Transit", [In-Transit Inventory Value],
    [Total Inventory Value]
)

