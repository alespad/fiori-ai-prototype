# Purchase Order Items - Goods Receipt Prototype

## Application Type
List Report + Object Page

## Main Entity
- **Business Object**: Purchase Order Item (for Goods Receipt)
- **Technical Name**: `PurchaseOrderItem`

## Filters (Filter Bar)

| Label | Type | Values / Notes |
|-------|------|----------------|
| Plant | Value Help (SelectDialog) | `001` - Main Plant, `002` - Secondary Plant |
| Supplier | Value Help (SelectDialog) | `1234` - ACME LLC, `5678` - COMPANY SRL |
| Purchase Order | Input | Free text input |
| Only Items without Errors | Switch | On/Off toggle |

**Note**: Plant and Supplier must use Value Help dialogs (F4 style with SelectDialog), NOT simple dropdowns.

## Table Columns

| Column | Property | Type |
|--------|----------|------|
| Plant | Plant | string |
| Supplier | Supplier | string |
| Purchase Order | PurchaseOrder | string |
| Delivery | Delivery | string |
| Material Description | MaterialDescription | string |
| Date | Date | date (format: DD.MM.YYYY) |

**Table behavior**:
- Table starts EMPTY - data loads only when user clicks "Go" button
- Rows are navigable (click navigates to Object Page detail)
- Include selection checkboxes for multi-select
- Include standard List Report toolbar icons (Export to Excel, Settings, Sort, Filter, Group) - visual only, no functionality needed

## Mock Data (8 records)

| Plant | Supplier | PurchaseOrder | Delivery | MaterialDescription | Date | HasError |
|-------|----------|---------------|----------|---------------------|------|----------|
| 001 | ACME LLC | 12345678 | 3000004 | Steel Beam HEB 200 | 2025-04-12 | false |
| 002 | ACME LLC | 12345679 | 3000005 | Aluminum Sheet 2mm | 2025-04-12 | false |
| 001 | COMPANY SRL | 12345677 | 3000006 | Industrial Valve DN50 | 2025-04-12 | true |
| 001 | ACME LLC | 12345680 | 3000007 | Copper Wire 4mm | 2025-04-15 | false |
| 002 | COMPANY SRL | 12345681 | 3000008 | Hydraulic Pump HP200 | 2025-04-18 | true |
| 001 | COMPANY SRL | 12345682 | 3000009 | Bearing SKF 6205 | 2025-04-20 | false |
| 002 | ACME LLC | 12345683 | 3000010 | Electric Motor 5kW | 2025-04-22 | false |
| 001 | ACME LLC | 12345684 | 3000011 | PVC Pipe DN100 | 2025-04-25 | true |

## Actions

### List Actions
| Action | Type | Requires Selection |
|--------|------|-------------------|
| Create GR | Button (Emphasized) | Yes - enabled only when rows are selected |

### Create GR Dialog
- **Title**: "Confirm Goods Receipt Creation"
- **Message**: "Please confirm the creation of the Goods Receipt for the selected items."
- **Fields**:
  - Confirmation Date (DatePicker, default: today)
- **Buttons**: Confirm, Cancel
- **On Confirm**: Show MessageToast "Goods Receipt {generated_number} created"

## Object Page (Detail View)

When clicking a table row, navigate to detail page showing:

### Header
- Title: Material Description
- Subtitle: Purchase Order number

### Sections

**General Information**
- Purchase Order
- Delivery
- Date

**Plant & Supplier**
- Plant (code + description)
- Supplier (code + name)

**Material**
- Material Description

**Status**
- Has Error: Yes/No (with semantic color: Error=red, None=green)

### Navigation
- Back button returns to list
- Edit button in header (visual only)

## Application Title
"Purchase Order Items - Goods Receipt"
