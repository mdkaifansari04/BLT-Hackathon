# Django Hackathon Management

A Django plugin for organizing and managing hackathons with GitHub repository integration.

## Features

- Create and manage hackathons with detailed information
- GitHub integration for tracking repositories and contributions
- Sponsor management with tiers and benefits
- Prize configuration and tracking
- Participant registration and management
- Real-time status updates (Upcoming, Ongoing, Ended)
- Responsive UI with dark mode support

## Requirements

- Python 3.11 or higher
- Django 4.0 or higher

## Installation

Install the plugin using pip:

```bash
pip install blt-hackathon
```

Or install from source for development:

```bash
git clone https://github.com/OWASP-BLT/BLT-Hackathon.git
cd BLT-Hackathon/plugin/django-hackathon
pip install -e .
```

## Configuration

### Step 1: Add to Installed Apps

Add `blt_hackathon` to your Django project's `INSTALLED_APPS` in `settings.py`:

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    
    # Add blt_hackathon
    'blt_hackathon',
    
    # Your other apps
]
```

### Step 2: Configure URL Routes

Include the hackathon URLs in your project's `urls.py`:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('hackathons/', include('blt_hackathon.urls')),
    # Your other URL patterns
]
```

### Step 3: Add Frontend Dependencies

The plugin requires Chart.js and Font Awesome to display charts and icons. Add these to your base template (usually `templates/base.html`):

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>Your Site</title>
    
    <!-- Font Awesome for icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    
    <!-- Your other CSS -->
    {% block extra_head %}{% endblock %}
</head>
<body>
    {% block content %}{% endblock %}
    
    <!-- Chart.js for charts -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    
    <!-- Your other scripts -->
    {% block scripts %}{% endblock %}
</body>
</html>
```

### Step 4: Run Migrations

Apply the database migrations:

```bash
python manage.py migrate blt_hackathon
```

### Step 4: Create Base Template

The plugin requires a base template at `templates/base.html` with the following blocks:

```django
<!DOCTYPE html>
<html lang="en">
<head>
    <title>{% block title %}{% endblock %}</title>
    <meta name="description" content="{% block description %}{% endblock %}">
    <meta name="keywords" content="{% block keywords %}{% endblock %}">
    <!-- Font Awesome 6.5.1 is required for icons -->
    <link rel="stylesheet" 
          href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" 
          integrity="sha512-DTOQO9RWCH3ppGqcWaEA1BIZOC6xxalwEsw9c2QQeAIftl+Vegovlnee1c9QX4TctnWMn13TZye+giMm8e2LwA==" 
          crossorigin="anonymous" 
          referrerpolicy="no-referrer" />
</head>
<body>
    {% block content %}{% endblock %}
</body>
</html>
```

## Usage

### Accessing the Hackathon Dashboard

Navigate to `http://your-domain.com/hackathons/` in your browser.

### Creating a Hackathon

1. Click the "Create Hackathon" button
2. Fill in the basic details (Name, Description, Start/End Time)
3. Configure registration settings and participant limits
4. Add banner image and rules
5. Save the hackathon

### Managing Repositories

1. Go to the hackathon detail page
2. Click "Add Org Repos" to link GitHub repositories
3. The plugin will automatically track PRs and contributions

### Adding Sponsors and Prizes

1. From the hackathon detail page, use the "Add Sponsor" button to register sponsors
2. Use "Add Prize" to configure prize tiers and descriptions

## Admin Interface

Hackathons can also be managed through the Django admin interface at `/admin/blt_hackathon/hackathon/`.

## Dependencies

The plugin automatically installs the following dependencies:
- Django (>=4.0, <6.0)
- requests (>=2.31.0)
- python-dateutil (>=2.9.0)
- Pillow (>=10.0.0)


## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines on how to contribute to this project.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Support

For issues, questions, or contributions:
- GitHub Issues: https://github.com/OWASP-BLT/BLT-Hackathon/issues
- Repository: https://github.com/OWASP-BLT/BLT-Hackathon