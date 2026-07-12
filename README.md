# Odoo Dev Snippets 🐍

> A powerful VS Code extension providing 50+ snippets for Odoo developers — Python models, XML views, fields, wizards, reports, email templates, server actions, and much more!

![Version](https://img.shields.io/badge/version-0.0.3-blue)
![VS Code](https://img.shields.io/badge/VS%20Code-1.20%2B-brightgreen)
![License](https://img.shields.io/badge/license-MIT-green)
![Odoo](https://img.shields.io/badge/Odoo-%2018%20|%2019-purple)

---

## Features

- ⚡ **Python Snippets** — Models, fields, computed methods, onchange, wizards, overrides
- 🖼️ **XML Snippets** — Form, tree, kanban, pivot, graph, activity, map, cohort views
- 🔘 **Button & Action Snippets** — Header buttons, smart buttons, server actions, window actions
- 🔗 **Relational Fields** — Many2one, One2many, Many2many
- 📋 **View Inheritance** — XPath based view extension
- 💬 **Chatter Support** — mail.thread integration ready
- 📧 **Email Templates** — Basic and with PDF attachment
- 📊 **Reports** — QWeb PDF report template
- ⏰ **Cron Jobs** — Python method and XML record
- 🔒 **Security** — Groups and record rules
- 🪵 **Logger** — Info, warning, error logging

---

## Installation

### From VS Code Marketplace
1. Open VS Code
2. Press `Ctrl+Shift+X` to open Extensions
3. Search for **"Odoo Dev Snippets"**
4. Click **Install**

### From VSIX (Manual)
1. Download the `.vsix` file
2. Open Extensions `Ctrl+Shift+X` → click `...` → **Install from VSIX**
3. Select the file and reload VS Code

---

## Python Snippets

### Model Snippets

| Prefix | Description |
|--------|-------------|
| `omodel` | Odoo Model class (`models.Model`) |
| `oinherit` | Inherit existing model (`_inherit`) |
| `owizard` | TransientModel (Wizard) class |

### Field Snippets

| Prefix | Description |
|--------|-------------|
| `ocompute` | Computed field with `@api.depends` |
| `oonchange` | Onchange method with decorator |
| `om2o` | Many2one relational field |
| `oo2m` | One2many relational field |
| `om2m` | Many2many relational field |
| `omulticompany` | Multi-company field (`company_id`) |
| `osequence` | Sequence integer field |

### Method Snippets

| Prefix | Description |
|--------|-------------|
| `obtn` | Button action method |
| `oconstraint` | `@api.constrains` with ValidationError |
| `odefaultget` | Override `default_get` |
| `ocreate` | Override `create` method |
| `owrite` | Override `write` method |
| `ounlink` | Override `unlink` with condition |
| `onamesearch` | Override `name_search` |
| `ocron` | Cron job method |

### Utility Snippets

| Prefix | Description |
|--------|-------------|
| `oerror` | Raise `UserError` exception |
| `osearch` | `self.env[].search([])` query |
| `osql` | Raw SQL query using `self.env.cr` |
| `olog` | Logger setup (info, warning, error) |
| `ologinfo` | Logger info message |
| `ologwarn` | Logger warning message |
| `ologerror` | Logger error message |
| `oendemail` | Send email from Python using template |

---

## XML Snippets

### View Snippets

| Prefix | Description |
|--------|-------------|
| `oform` | Complete Form View record |
| `otree` | Tree / List View record |
| `okanban` | Kanban View record |
| `osearchview` | Search View with filter and group by |
| `opivot` | Pivot View |
| `ograph` | Graph View (bar / line / pie) |
| `oactivityview` | Activity View |
| `omapview` | Map View |
| `ocohort` | Cohort View |
| `oinherit` | View inherit with XPath |

### Action & Menu Snippets

| Prefix | Description |
|--------|-------------|
| `oaction` | `ir.actions.act_window` record |
| `omenu` | `menuitem` tag |
| `oserveraction` | Server Action — Python code |
| `oserveractionurl` | Server Action — URL redirect |
| `oserveractioncreate` | Server Action — Create record |

### Widget Snippets

| Prefix | Description |
|--------|-------------|
| `obtnheader` | Header with button and statusbar |
| `osmartbtn` | Smart Button (`oe_stat_button`) |
| `ostatusbar` | Statusbar widget for state field |
| `omonetary` | Monetary field with currency |
| `oprogress` | Progress bar widget |
| `om2mtags` | Many2many tags widget |
| `opriority` | Priority widget (stars) |
| `ocolorpicker` | Color picker widget |

### Layout Snippets

| Prefix | Description |
|--------|-------------|
| `onote` | Notebook with page tab |
| `ogroup2` | Two-column group layout |
| `ochatter` | Chatter widget (message, activity, follower) |
| `omodulexml` | Base XML file wrapper (`<odoo><data>`) |
| `odomainfilter` | Domain filter button in search view |

### Other Snippets

| Prefix | Description |
|--------|-------------|
| `oemailtemplate` | Email Template (mail.template) |
| `oemailattachment` | Email Template with PDF Attachment |
| `oreport` | QWeb PDF Report template |
| `ocronxml` | Cron Job XML record |
| `osequencexml` | Sequence XML record |
| `ogroup` | Security Group (res.groups) |
| `oresrule` | Record Rule (ir.rule) |

---

## Examples

### `omodel` — Complete Model

```python
from odoo import models, fields, api

class SaleOrder(models.Model):
    _name = 'sale.order'
    _description = 'Sale Order'

    name = fields.Char(string='Name', required=True)
    # cursor lands here
```

### `ocompute` — Computed Field

```python
total_amount = fields.Float(
    string='Total Amount',
    compute='_compute_total_amount'
)

@api.depends('order_line')
def _compute_total_amount(self):
    for rec in self:
        rec.total_amount = # cursor lands here
```

### `ocreate` — Create Override

```python
@api.model_create_multi
def create(self, vals_list):
    for vals in vals_list:
        # modify vals if needed
    records = super().create(vals_list)
    # cursor lands here
    return records
```

### `oform` — Form View

```xml
<record id="sale_order_form_view" model="ir.ui.view">
    <field name="name">sale.order.form</field>
    <field name="model">sale.order</field>
    <field name="arch" type="xml">
        <form string="Sale Order">
            <sheet>
                <group>
                    <field name="name"/>
                    <!-- cursor lands here -->
                </group>
            </sheet>
        </form>
    </field>
</record>
```

### `oemailtemplate` — Email Template

```xml
<record id="email_template_sale" model="mail.template">
    <field name="name">Sale Order Template</field>
    <field name="model_id" ref="model_sale_order"/>
    <field name="subject">Sale Order Confirmation</field>
    <field name="email_from">${object.company_id.email}</field>
    <field name="email_to">${object.partner_id.email}</field>
    <field name="body_html" type="html">
        <div>
            <p>Dear <t t-out="object.partner_id.name"/>,</p>
            <p>Your order has been confirmed.</p>
        </div>
    </field>
</record>
```

### `ocronxml` — Cron Job

```xml
<record id="ir_cron_auto_confirm" model="ir.cron">
    <field name="name">Auto Confirm Orders</field>
    <field name="model_id" ref="model_sale_order"/>
    <field name="state">code</field>
    <field name="code">model._cron_auto_confirm()</field>
    <field name="interval_number">1</field>
    <field name="interval_type">days</field>
    <field name="numbercall">-1</field>
    <field name="active" eval="True"/>
</record>
```

---

## How to Use

1. Open a **Python** or **XML** file in VS Code
2. Type the snippet **prefix** (e.g. `omodel`)
3. Press **Tab** or **Enter** to expand
4. Use **Tab** again to jump between placeholders
5. Fill in your values and you're done!

> 💡 **Pro Tip:** Just type `o` to see ALL Odoo snippets in the IntelliSense dropdown at once!

---

## Requirements

- VS Code `1.20.0` or higher
- Compatible with all Odoo versions: `14.0`, `15.0`, `16.0`, `17.0`, `18.0`, `19.0`

---

## Extension Settings

This extension does not add any VS Code settings.

---

## Author

**Aman Kumar Singh**
- GitHub: [@amankum02](https://github.com/amankum02)
- LinkedIn: [Aman Kumar Singh](https://linkedin.com/in/aman-kumar-singh-5b163b294)
- Email: as2732044@email.com

---

## Contributing

Contributions are welcome! If you want to add new snippets or fix a bug:

1. Fork this repository
2. Create a new branch: `git checkout -b feature/my-snippet`
3. Add your snippet to `snippets/python.json` or `snippets/xml.json`
4. Submit a Pull Request

When submitting a snippet, please include:
- A clear `prefix`
- A helpful `description`
- Proper `$1`, `$2` tab stops

---

## Snippet Format Reference

```json
"Snippet Name": {
    "prefix": "oprefix",
    "body": [
        "line one ${1:placeholder}",
        "line two ${2:placeholder}",
        "${0}"
    ],
    "description": "Short description of what this snippet does"
}
```

---

## Changelog

### 0.0.3 — Latest
- Added Python overrides: `create`, `write`, `unlink`, `default_get`, `name_search`
- Added `@api.constrains` snippet
- Added Logger snippets (info, warning, error)
- Added Raw SQL query snippet
- Added Multi-company and Sequence field snippets
- Added Server Action snippets (code, url, create)
- Added Email Template snippets (basic + with attachment)
- Added Pivot, Graph, Activity, Map, Cohort view snippets
- Added Widget snippets: monetary, progress, priority, color picker, many2many tags
- Added Cron Job XML snippet
- Added Sequence XML snippet
- Added Security Group and Record Rule snippets
- Added QWeb PDF Report snippet

### 0.0.2 — Latest
- Update vs code version compatiblity
- Added keyword

### 0.0.1 — Initial Release
- Python model, field, compute, and onchange snippets
- XML form, tree, kanban, and search view snippets
- Button, action, and menu snippets
- View inheritance (XPath) snippet
- Smart button and chatter snippets
- Wizard (TransientModel) snippet

---

## Known Issues

No known issues at this time. Please [open an issue](https://github.com/amankum02/odoo-snippets/issues) if you find one.

---

## License

MIT License — Copyright (c) 2025 Aman Kumar Singh

Free to use, modify, and distribute.

---

**Made with ❤️ by [Aman Kumar Singh](https://github.com/amankum02) for the Odoo Developer Community**