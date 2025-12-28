# djongo-patched

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)

## Django 5.x Compatible Fork of Djongo

This is a patched fork of [djongo](https://github.com/doableware/djongo) with full Django 5.x compatibility. Djongo is the only connector that lets you use Django with MongoDB **without** changing the Django ORM.

### Key Features

- ✅ **Django 5.2.7 Compatible** - Fully tested with Django 5.x
- ✅ **Production Ready** - All patches tested and verified
- ✅ **Zero ORM Changes** - Use MongoDB as a backend without modifying Django ORM
- ✅ **Admin GUI Support** - Use Django Admin to manage MongoDB documents

### Patches Included

This fork includes critical patches for Django 5.x compatibility:

1. **Abstract Model Instantiation** - Helper method for instantiating abstract models
2. **SQL Parser VALUES Token** - sqlparse compatibility for INSERT operations
3. **ORDER BY/GROUP BY Handling** - Support for modern sqlparse tokenization
4. **Positional ORDER BY** - Support for Django 5.x positional column references

For detailed patch documentation, see [DJANGO_5_COMPATIBILITY_PATCH.md](./DJANGO_5_COMPATIBILITY_PATCH.md)

## Installation

### From GitHub

```bash
pip install git+https://github.com/zintlr/djongo-patched.git
```

### From Local Clone

```bash
git clone https://github.com/zintlr/djongo-patched.git
cd djongo-patched
pip install -e .
```

## Usage

Add to your Django `settings.py`:

```python
DATABASES = {
    'default': {
        'ENGINE': 'djongo',
        'NAME': 'your-db-name',
        'CLIENT': {
           'host': 'your-db-host',
        }
    }
}
```

Run migrations:
```bash
python manage.py makemigrations
python manage.py migrate
```

## Requirements

- Python 3.10 or higher
- Django 5.x
- MongoDB 3.4 or higher (3.6+ recommended for nested queries)
- PyMongo 3.12.3

## Version

Current version: **1.3.8-patched**

Based on djongo 1.3.6 with Django 5.2.7 compatibility patches.

## Changes from Upstream

See [DJANGO_5_COMPATIBILITY_PATCH.md](./DJANGO_5_COMPATIBILITY_PATCH.md) for complete details on all modifications.

### Modified Files:
- `djongo/__init__.py` - Version bump
- `djongo/models/fields.py` - Abstract model helper
- `djongo/sql2mongo/query.py` - VALUES, ORDER BY, GROUP BY handling
- `djongo/sql2mongo/converters.py` - Enhanced converters
- `djongo/sql2mongo/sql_tokens.py` - Positional ORDER BY support

## Contributing

This is a production fork maintained for Django 5.x compatibility. For issues specific to the patches, please open an issue in this repository.

For general djongo issues, see the [upstream repository](https://github.com/doableware/djongo).

## License

AGPL v3 (inherited from upstream djongo)

## Credits

- Original djongo: [doableware/djongo](https://github.com/doableware/djongo)
- Django 5.x patches: Zintlr Team
- Maintained by: [@zintlr](https://github.com/zintlr)

---

**Note:** This fork is specifically patched for Django 5.x. If you need Django 4.x or earlier support, use the official djongo package.
