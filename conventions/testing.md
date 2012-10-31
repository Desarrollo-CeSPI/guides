# Convenciones respecto al testing

## Fixtures

Rails por defecto genera fixtures. Estos fixtures define las claves `one` y
`two`.

* Redefinir `one` y `two` según el modelo que se esté definiendo, por
  ejemplo, si tenemos el modelo `Article`, definir `article_one` y
  `article_two`

## Unit

Suponiendo el siguiente modelo, será explicado con *EDD* (Example Driven Development):

```ruby
class Article < ActiveRecord::Base
  # attributes
  attr_accessible :content, :title

  # validations
  validates :content, present: true
  validates :title, present: true, uniqueness: true

  def this_method_does_something
    # do something
  end

  def to_s
    # return some string
  end
end

```

Debería definirse un `TestCase` de la siguiente forma:

```ruby
require 'test_helper'

class ArticleTest < ActiveSupport::TestCase
  # test validations

  test 'present attributes' do
    article = Article.new

    assert article.invalid?

    assert_equal 2, article.errors.size

    assert_present article.errors[:content]
    assert_present article.errors[:title]
  end

  test 'unique attributes' do
    article = Article.new
    article.content = articles(:article_one).content
    article.title = articles(:article_one).title

    assert article.invalid?

    assert_equal 1, article.errors.size

    assert_present article.errors[:title]
    assert_equal I18n.t('activerecord.errors.messages.invalid'), application.errors[:title].join(';')
  end

  # test methods

  test 'Article#this_method_does_something' do
    # test this_method_does_something
  end

  test 'Article#to_s' do
    # test to_s
  end
end

```

En resumen:

* Testear en el mismo orden que se definen las secciones del modelo (Ver [models](https://github.com/Desarrollo-CeSPI/guides/blob/master/conventions/models.md))
* Testear los métodos en **orden alfabético**
* No testear nada que sea provisto por el framework, como por ejemplo asociaciones.

## Functional

Los tests funcionales auto-generados por rails sirven como ayuda, pero no son
completos, debido a que sólo testean la funcionalidad por el camino feliz
(cosa que es obvia porque por defecto los modelos no tienen validaciones). He
aquí algunos guidelines para mejorar estos tests:

* Si el modelo tiene validaciones, crear un test funcional por cada tipo de
  validación, por ejemplo si tenemos atributos `present`, crear un test
  funcional para los `present`, si tenemos atributos `unique`, crear un test
  funcional para los `unique`, tanto para el `create` como para el `update`.
* Al igual que los controllers, el orden de los tests es como sigue:
  * `index`
  * `show`
  * `new`
  * `edit`
  * `create`
  * `update`
  * `destroy`
* Las acciones que se definan en nuestros controllers deben testearse después,
  en el mismo orden que se definan en el controller (obviamente en **orden
  alfabético**

