<<<<<<< HEAD
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
=======
# odoo-snippets README

This is the README for your extension "odoo-snippets". After writing up a brief description, we recommend including the following sections.

## Features

Describe specific features of your extension including screenshots of your extension in action. Image paths are relative to this README file.

For example if there is an image subfolder under your extension project workspace:

\!\[feature X\]\(images/feature-x.png\)

> Tip: Many popular extensions utilize animations. This is an excellent way to show off your extension! We recommend short, focused animations that are easy to follow.

## Requirements

If you have any requirements or dependencies, add a section describing those and how to install and configure them.

## Extension Settings

Include if your extension adds any VS Code settings through the `contributes.configuration` extension point.

For example:

This extension contributes the following settings:

* `myExtension.enable`: Enable/disable this extension.
* `myExtension.thing`: Set to `blah` to do something.

## Known Issues

Calling out known issues can help limit users opening duplicate issues against your extension.

## Release Notes

Users appreciate release notes as you update your extension.

### 1.0.0

Initial release of ...

### 1.0.1

Fixed issue #.

### 1.1.0

Added features X, Y, and Z.

---

## Working with Markdown

You can author your README using Visual Studio Code. Here are some useful editor keyboard shortcuts:

* Split the editor (`Cmd+\` on macOS or `Ctrl+\` on Windows and Linux).
* Toggle preview (`Shift+Cmd+V` on macOS or `Shift+Ctrl+V` on Windows and Linux).
* Press `Ctrl+Space` (Windows, Linux, macOS) to see a list of Markdown snippets.

## For more information

* [Visual Studio Code's Markdown Support](http://code.visualstudio.com/docs/languages/markdown)
* [Markdown Syntax Reference](https://help.github.com/articles/markdown-basics/)

**Enjoy!**
>>>>>>> 557b2bf95e0cc0bac0ea32ecf5a8e1f37891c2af
