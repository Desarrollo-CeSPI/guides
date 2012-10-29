# Convenciones para los controllers

Será explicado con *EDD* (Example Driven Development):

```ruby
class ArticleController < ApplicationController
  before_filter :authenticate_user!
  before_filter :find_something!
  respond_to :html, :json

  def index
    # ...
    respond_with @articles
  end

  def show
    # ...
    respond_with @article
  end

  def new
    # ...
    respond_with @article
  end

  def edit
    # ...
    respond_with @article
  end

  def create
    # ...
    respond_with @article
  end

  def update
    # ...
    respond_with @article
  end

  def destroy
    # ...
    respond_with @article
  end

  def a_new_action
    # ...
    respond_with @article
  end

  def another_action
    # ...
    respond_with @article
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
* Los [responders](http://blog.plataformatec.com.br/2009/08/embracing-rest-with-mind-body-and-soul/)
  van luego de los filtros (por el **orden alfabético**). Más sobre [responders](https://github.com/rails/rails/blob/master/actionpack/lib/action_controller/metal/mime_responds.rb)
* Las acciones por defecto deben seguir el orden que impone el `scaffold
  generator` y es el detallado en el ejemplo
* Las acciones definidas por el usuarios deben ir en **orden alfabético**
  luego de `destroy`

