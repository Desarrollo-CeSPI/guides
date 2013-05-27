# Toolbox

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be
interpreted as described in [RFC 2119](http://www.ietf.org/rfc/rfc2119.txt).

## General

### Authentication

* When developing applications for UNLP you **must** use
[omniauth-saml](https://github.com/PracticallyGreen/omniauth-saml).
* When developing applications with third-party sign in you **must** use
[omniauth](https://github.com/intridea/omniauth).

### Configuration files

You **should** use [miniconfig](https://github.com/patriciomacadden/miniconfig) **OR** [rails_config](https://github.com/railsjedi/rails_config).

### Database

You **must** use [activerecord](https://github.com/rails/rails/tree/master/activerecord).

### I18n

You **must** use [i18n](https://github.com/svenfuchs/i18n) (bundled with rails).

### Profiling

You **should** use [rack-mini-profiler](https://github.com/SamSaffron/MiniProfiler/tree/master/Ruby).

## API

You **must** use [Sinatra](https://github.com/sinatra/sinatra) 

You **must** follow [API Standard Guide](https://github.com/ncuesta/api-doc)

## Small apps

You **must** use [Sinatra](https://github.com/sinatra/sinatra) 

## Rails specific

### Audit

You **must** use [paper_trail](https://github.com/airblade/paper_trail)

### Authentication

When developing applications with its own authentication you **must** use
[devise](https://github.com/plataformatec/devise).

### Authorization

You **must** use [pundit](https://github.com/elabs/pundit).

### Deployment

* You **must** use [capistrano](https://github.com/capistrano/capistrano).
* You **must** use [capistrano-extras](https://github.com/patriciomacadden/capistrano-extras).
* You **must** use [capistrano-rbenv](https://github.com/yyuu/capistrano-rbenv).
* You **must** use [unicorn](https://github.com/defunkt/unicorn).

### Enumerated attributes

You **must** use [enumerize](https://github.com/brainspec/enumerize).

### Forms

You **must** use [simple_form](https://github.com/plataformatec/simple_form).

### I18n extensions

You **must** use [rails-i18n](https://github.com/svenfuchs/rails-i18n) for
common rails strings.

### Pagination

You **must** use [kaminari](https://github.com/amatsuda/kaminari).

### PDF

You **should** use [PDFKit](https://github.com/pdfkit/pdfkit) **OR**
[Prawn](https://github.com/prawnpdf/prawn).

### Permalinks

You **must** use [kaminari](https://github.com/FriendlyId/friendly_id).

### Scaffold

You **should** use
[nice_generators](https://github.com/patriciomacadden/nice_generators).

### Serialization

You **must** use [active_model_serializers](https://github.com/rails-api/active_model_serializers).

### Testing

You **must** use [factory_girl](https://github.com/thoughtbot/factory_girl).

### Uploads

You **must** use [carrierwave](https://github.com/jnicklas/carrierwave).

### Workflow

You **should** use [micromachine](https://github.com/soveran/micromachine)
**OR** [workflow](https://github.com/geekq/workflow).
