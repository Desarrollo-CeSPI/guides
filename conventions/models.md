# Convenciones para los modelos

Será explicado con *EDD* (Example Driven Development):

```ruby
class Article < ActiveRecord::Base
  include SomeModule

  # attributes
  attr_accessible :content, :title
  attr_reader :a_reader_attribute
  attr_writer :a_writer_attribute

  # callbacks
  before_save :do_something

  # scopes
  default_scope order('created_at asc')
  scope :published, where('published = true')

  # validations
  validates :title, presence: true, uniqueness: true

  def self.some_class_method
    # do something
  end

  def some_method
    # do something
  end

  def to_s
    title
  end

  protected

  def a_protected_method
    # do something
  end

  private

  def do_something
  end
end

```

La forma de organizar el código en las clases es la siguiente:

* La inclusión (`include`) y extensión (`extend`) de módulos se declara al
  comienzo
* Luego lo sigue una sección donde se usan las sentencias relativas a los
  atributos (`attributes`)
  * Notar que tanto las sentencias (`attr_accesible`, `attr_reader` y
    `attr_writer` en este caso) como los simbolos que representan a los
    atributos (`:content`, `:title`, etc.) se escriben *alfabeticamente*
* Luego se especifican los `callbacks`, tambien en *orden alfabético*
* Le siguen los `scopes`
* Luego las `validations`
* Por último los métodos:
  * Primero los métodos de *clase*, siempre en *orden alfabético*
  * Luego los métodos de *instancia*, siempre en *orden alfabético*
  * Los métodos protegidos (`protected`) van después, siempre en *orden
    alfabético*
  * Y por último los métodos privados (`private`), siempre en *orden
    alfabético*

## Recomendaciones

* No usar métodos protegidos (Ver [Protect your privates](http://robots.thoughtbot.com/post/31794893208/protect-your-privates))
* Si la clase tiene muchos `callbacks` o algún `callback` es demasiado largo,
  usar *observers*

