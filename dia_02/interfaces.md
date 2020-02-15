# Interfaces

Uma **interface** é uma coleção de assinaturas de metódos que um tipo (type) pode implementar usando metodos. Portanto uma **inteface** define não declara o comportamento do objeto do tipo type.

A Principal ultilidade de uma interface é apenas fornecer assinaturas de metodo consistindo no nome do do método, argumentos de entrada e tipos de retorno. É de responsabilidade de um método (ex: *struct*) declarar os métodos e implementá-los.

Para exemplificar vamos usar os mesmos dados que usamos para criar métodos.

```go
package main

// GEO ...
type GEO interface {
	CalculaArea() float64
	CalculaPerimetro() float64
}

type area struct {
	Largura float64
	Altura  float64
}

func (r *area) CalculaArea() float64 {
	res := r.Largura * r.Altura
	return res
}

func (r *area) CalculaPerimetro() float64 {
	res := 2*r.Largura + 2*r.Altura
	return res
}

func printMedida(g GEO) {
	fmt.Println(g)
	fmt.Println(fmt.Sprintf("Area: %0.2f", g.CalculaArea()))
	fmt.Println(fmt.Sprintf("Perim: %0.2f", g.CalculaPerimetro()))
}

func main() {
	a := area{
		Altura:  10,
		Largura: 5,
	}

	printMedida(&a)
}
```