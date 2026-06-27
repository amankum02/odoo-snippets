# Odoo Snippets 🐍

> A powerful VS Code extension providing snippets for Odoo developers — Python models, XML views, fields, wizards, and much more!

![Version](https://img.shields.io/badge/version-0.0.1-blue)
![VS Code](https://img.shields.io/badge/VS%20Code-1.60%2B-brightgreen)
![License](https://img.shields.io/badge/license-MIT-green)
![Odoo](https://img.shields.io/badge/Odoo-14%20|%2015%20|%2016%20|%2017-purple)

---

## Features

- ⚡ **Python Snippets** — Models, fields, computed methods, onchange, wizards
- 🖼️ **XML Snippets** — Form, tree, kanban, and search views
- 🔘 **Button & Action Snippets** — Header buttons, smart buttons, window actions
- 🔗 **Relational Fields** — Many2one, One2many, Many2many
- 📋 **View Inheritance** — XPath based view extension
- 💬 **Chatter Support** — mail.thread integration ready

---

## Installation

### From VS Code Marketplace
1. Open VS Code
2. Press `Ctrl+Shift+X` to open Extensions
3. Search for **"Odoo Snippets"**
4. Click **Install**

### From VSIX (Manual)
1. Download the `.vsix` file
2. Open Extensions `Ctrl+Shift+X` → click `...` → **Install from VSIX**
3. Select the file and reload VS Code

---

## Python Snippets

| Prefix | Description |
|--------|-------------|
| `omodel` | Odoo Model class (`models.Model`) |
| `ocompute` | Computed field with `@api.depends` |
| `oonchange` | Onchange method with decorator |
| `om2o` | Many2one relational field |
| `oo2m` | One2many relational field |
| `om2m` | Many2many relational field |
| `obtn` | Button action method |
| `oerror` | Raise `UserError` exception |
| `osearch` | `self.env[].search([])` query |
| `owizard` | TransientModel (Wizard) class |

### Example — `omodel`

Type `omodel` and press **Tab**:

```python
from odoo import models, fields, api

class SaleOrder(models.Model):
    _name = 'sale.order'
    _description = 'Sale Order'

    name = fields.Char(string='Name', required=True)
    # cursor lands here
```

### Example — `ocompute`

Type `ocompute` and press **Tab**:

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

---

## XML Snippets

| Prefix | Description |
|--------|-------------|
| `oform` | Complete Form View record |
| `otree` | Tree / List View record |
| `okanban` | Kanban View record |
| `osearchview` | Search View with filter and group by |
| `oaction` | `ir.actions.act_window` record |
| `omenu` | `menuitem` tag |
| `obtnheader` | Header with button and statusbar widget |
| `osmartbtn` | Smart Button (`oe_stat_button`) |
| `onote` | Notebook with page tab |
| `ogroup2` | Two-column group layout |
| `oinherit` | View inherit with XPath |
| `ochatter` | Chatter widget (message, activity, follower) |
| `omodulexml` | Base XML file wrapper (`<odoo><data>`) |

### Example — `oform`

Type `oform` and press **Tab**:

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

### Example — `oinherit`

Type `oinherit` and press **Tab**:

```xml
<record id="sale_order_form_view_inherit" model="ir.ui.view">
    <field name="name">sale.order.form.inherit</field>
    <field name="model">sale.order</field>
    <field name="inherit_id" ref="sale.view_order_form"/>
    <field name="arch" type="xml">
        <xpath expr="//field[@name='partner_id']" position="after">
            <!-- cursor lands here -->
        </xpath>
    </field>
</record>
```

---

## How to Use

1. Open a **Python** or **XML** file in VS Code
2. Type the snippet **prefix** (e.g. `omodel`)
3. Press **Tab** or **Enter** to expand
4. Use **Tab** again to jump between placeholders
5. Fill in your values and you're done!

> 💡 **Pro Tip:** Type `o` to see all available Odoo snippets in the IntelliSense dropdown at once!

---

## Requirements

- VS Code `1.60.0` or higher
- Compatible with Odoo `19.0`

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