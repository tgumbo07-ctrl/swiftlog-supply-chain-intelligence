# AnalystLab Africa Guidance — SwiftLog Data Gaps

Source: AnalystLab Africa Slack response from Thomas Mutua, supplied by Takudzwa Gumbo.

## Supplier relationship
The supplied data has no direct Supplier relationship to Products or Shipments. Treat Suppliers as a standalone reference table unless a documented assumption is created. Supplier performance should therefore be discussed conceptually rather than fabricated.

## Warehouse capacity
Warehouse capacity is not supplied. Permitted proxies include total inventory quantity, unique products and shipment volume. Any such metric must be labelled as estimated/proxy utilisation rather than true capacity utilisation.

## Inventory records
Repeated Warehouse–Product rows represent stock movements, not records to remove as duplicates. Aggregate stock quantity by Warehouse–Product for reporting where appropriate.

## Data dictionary
The dictionary is intentionally simplified. Infer reasonable meanings from column names and structure, document assumptions, limitations and data-collection recommendations.
