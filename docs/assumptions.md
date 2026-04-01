# 📌 Assumptions

- **Total Inventory Value** is calculated as the sum of On-Hand, WIP, and In-Transit value fields available in the dataset.
- **Total Inventory Quantity** is calculated as the sum of On-Hand, WIP, and In-Transit quantity fields.
- **Inventory Type** is treated as a reporting concept derived from available quantity and value columns, rather than a direct source category field.
- **Average DOH** is calculated using the source DOH field.
- Missing descriptive values were handled carefully to avoid distorting the overall inventory position.
- Dashboard design was focused on business usability, KPI clarity, and exception visibility.
