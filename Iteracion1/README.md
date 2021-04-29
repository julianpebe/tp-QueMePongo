Primera Iteración QueMePongo
==============

[Enunciado](https://docs.google.com/document/d/1k1f-9AuIohlBGB2soSNePJ6jLxM37_tZeSD-hW_esIQ/edit)

Esta entrega se da a partir de una puesta en común con el grupo 20, por eso es igual que [esta entrega](https://github.com/nicolas-m-gomez/QueMePongo/tree/master/primera-iteracion)

Primero, las categorias, los tipos de prenda y los materiales fueron modelados con Enum ya que ambas representan formas de clasificación finitas para las prendas.

Además, para que una prenda no tenga una categoria que no se corresponde con el Tipo de prenda, la categoria es un atributo del TipoPrenda.

```
enum Categoria {
  PARTE_SUPERIOR,
  CALZADO,
  PARTE_INFERIOR,
  ACCESORIO,
}

enum TipoPrenda {
  CAMISA(Categoria.PARTE_SUPERIOR),
  REMERA(Categoria.PARTE_SUPERIOR),
  MUSCULOSA(Categoria.PARTE_SUPERIOR),
  POLERA(Categoria.PARTE_SUPERIOR),
  PANTALON(Categoria.PARTE_INFERIOR),
  ZAPATO(Categoria.CALZADO),
  BOTAS(Categoria.CALZADO),
  ANTEOJOS(Categoria.ACCESORIO),
  
  private Categoria categoria;
  
  public TipoPrenda(Categoria categoria) {
    this.categoria = categoria;
  }
  
  public Categoria getCategoria() {
    return categoria;
  }
}

enum Material {
  CUERO,
  ALGODON,
  JEAN,
}
```

Respecto a los colores, se definió como una clase formada por tres atributos: rojo, verde y azul (red, green and blue o RGB) para poder representar colores con un límite mucho mayor al que se podría con un string.
```
public class Color {
  private Integer rojo;
  private Integer verde;
  private Integer azul;
  
  public Color(Integer rojo, Integer verde, Integer Azul) {
    this.rojo = rojo;
    this.verde = verde;
    this.azul = azul;
  }
}
```

Finalmente, para modelar las prendas con los atributos que se especificaron obligatorios, se podría hacer de la siguiente manera:
```
public class Prenda {
  private TipoPrenda tipo;
  private Material material;
  private Color colorPrincipal;
  private Color colorSecundario;
  
  public Prenda(TipoPrenda tipo, Material material, Color colorPrincipal, Color colorPrimario) {
    if(tipo == null || material == null || colorPrincipal == null) {
      throw new AtributoNoDefinidoException();
    }

    this.tipo = tipo;
    this.material = material;
    this.colorPrincipal = colorPrincipal;
    this.colorSecundario = colorSecundario;
  }

  public Categoria getCategoria() {
    return this.tipo.getCategoria();
  }
```
Diagrama de Clases
![diagrama](http://www.plantuml.com/plantuml/png/VL3BReCm4BpxAtnifIQVK6LBt8e8Oik6IowLHQo8ok3AWHuQzT-xcn13Bxt0F3IUqMxEWut3s7cMUNi-SnLTVxJymZYlsiymqG4XAgKTN6ojvzq4KCk23v4tz5MnxMnimr_Lk6RiZtSTWwU0KNvoGo8FZ-o7iOO6J4dgptkqNUGnV8G5_NBnw1RSVe-UuguVktdXXSfgeUKJ0YZUv5Rk4Uq4q6-zNgV8F8ao2dGbtasjXCwbfaUWEC1M9YlVlzujo39X99Bqrdoosm0eSmC8j2Y59b3M9giBUHMLB6wYWdq5nNNV0HHKLFOYAp3uHql8dJJJwEK5cpkYUZRLhbRFjnF-Aymx5sew7YDx6Kz56zJ6ply2)