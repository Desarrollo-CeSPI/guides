# Convenciones para los controllers

Será explicado con *EDD* (Example Driven Development):

```ruby
class ArticleController < ApplicationController
  before_filter :authenticate_user!
  before_filter :find_something!

  def index
    # ...
  end

  def show
    # ...
  end

  def new
    # ...
  end

  def edit
    # ...
  end

  def create
    # ...
  end

  def update
    # ...
  end

  def destroy
    # ...
  end

  private

  def find_something!
    @something = Something.find(params[:something_id])
  end
end
```

La forma de organizar el código en las clases es la siguiente:

* Los filtros (2 `before_filter` en este caso) se declaran al comienzo:
  * En **orden alfabético** (primero `authenticate_user!` y luego
  `find_something!`)
  * Los filtros deben ser métodos privados (`private`) (ver al final de la
    clase)
  * Usar `only` y `except` en el caso que corresponda
* Las acciones por defecto deben seguir el orden que impone el `scaffold
  generator` y es el detallado en el ejemplo
* Las acciones definidas por el usuarios deben ir en *orden alfabético* luego
  de `destroy`

