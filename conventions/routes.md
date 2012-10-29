# Convenciones para las routes

Será explicado con *EDD* (Example Driven Development):

```ruby
SomeApplication::Application.routes.draw do
  resources :articles do
    collection do
      get :published
    end

    member do
      put :publish
      put :unpublish
    end

    resources :comments
  end

  resource :profile, only: [:edit, :update]
end

```

La forma de organizar el código en las clases es la siguiente:

* Definir los recursos en **orden alfabético**
* Definir rutas para `collection` y `member` también en orden **alfabético**:
  * Primero `collection`
  * Luego `member`
  * Luego `resources` (en **orden alfabético**)
  * Los métodos `get`, `post`, etc., también en **orden alfabético**
* Usar los **verbos http** de forma consciente, es decir, usarlos según [REST](http://es.wikipedia.org/wiki/Representational_State_Transfer)
* Para recursos únicos (en el ejemplo, `profile` es un recurso único), usar
  `resource` en vez de `resources`
* Si una ruta no se usa, no hay que generarla, por lo tanto hay que usar `only`
  o `except`:
  * Usar `only` cuando hay pocas rutas a definir
  * Usar `except` cuando hay pocas rutas por excluir

