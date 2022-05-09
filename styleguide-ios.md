# Vortigo iOS Styleguide

## Objetivos

- Facilitar o entendimento de novos membros
- Facilitar a manutenção do código
- Reduzir erros simples de desenvolvimento
- Manter as discussões dos PRs/MRs focadas na lógica e construção da tarefa

## Styleguide

### Nomenclatura

Todas as declarações devem ser auto-explicativas e consistir de palavras do Inglês Americano, além de formar frases legíveis e que façam sentido quando lidas.
Usar nomes descritivos torna o código mais simples de ler e entender. Esta styleguide é apenas uma extensão das diretrizes oficiais Swift API Design Guidelines e não deve contradizer o que consta no documento.

#### Um bom nome não deve precisar de comentários
Exemplos:
##### Não preferível
```swift
let countdown = 100 // Contagem para o natal (em dias)
```

##### Correto
```swift
let countdownForChristmasInDays = 100
```

#### Priorizar a clareza ao invés da brevidade
Exemplos:
##### Não preferível
```swift
let i =  0 // evitar palavras sem significado
let cat = "cat or category?" // evitar siglas
let url =  "www.some-url.com?" // qual url?
```

##### Correto
```swift
let count = 0
let theCat = "O gato"
let category = "Categoria"
let imageURL = "www.image-url.com"
```

#### Usar `UpperCamelCase` para types e protocols. Usar `lowerCamelCase` para o restante
Exemplos:
```swift
protocol Vehicle { }

final class Car: Vehicle {
	enum Brand {
		case ferrari
		case honda
		case hyundai
	}
    
	var brand: Brand = .honda
	var carName = "Any car name"
}

struct Vehicle { }

let myCar = Car()
```

#### Nomear booleans como isTrackable, hasMedicines, etc, para deixar claro que são booleans
Exemplos:
##### Não preferível
```swift
struct Product {
	let favorited = false
}
```

##### Correto
```swift
struct Product {
	let isFavorited = false
}
```

#### Usar nomes baseados no propósito e não no tipo
Exemplos:
##### Não preferível
```swift
let view = UIView()
let string = "any-text"
```

##### Correto
```swift
let footerView = UIView()
let fullName = "John Doe"
```

#### Em caso de ambiguidade, incluir uma dica sobre o tipo
Exemplos:
##### Não preferível
```swift
let title: UILabel
let confirm: UIButton
```

##### Correto
```swift
let titleLabel: UILabel 
let confirmButton: UIButton
```

#### Os nomes de `class/struct` devem ser um substantivo ou uma frase nominal. Preferencialmente não ser um verbo
Exemplos:
##### Não preferível
```swift
class Buy { }
```

##### Correto
```swift
class Purchase { }
```

#### Os nomes de funções de manipulação de eventos devem ser nomeados usando o `past-tense`
Exemplos:
##### Não preferível
```swift
func modelChanged() { }
func handleCancelButtonTap() { }
```

##### Correto
```swift
func modelDidChange() { }
func didTapCancelButton() { }
```

#### Evitar prefixos do `Objective-C`
Exemplos:
##### Não preferível
```swift
class VTLoginViewController { }
```

##### Correto
```swift
class LoginViewController { }
```

#### Questionar se os argumentos passados por parâmetro de um `delegate` fazem sentido. Muitas vezes é comum colocar `self` como primeiro argumento do `delegate`
Exemplos:
##### Não preferível
```swift
protocol LoginViewControllerDelegate: AnyObject {  
	func didTapLoginButton(_ viewController: UIViewController, button: UIButton)
}
```

##### Correto
```swift
protocol LoginViewControllerDelegate: AnyObject {  
	func didTapLoginButton()
}
```

### Nomes dos Arquivos

####  O nome do arquivo deve conter o mesmo nome da classe, struct etc, que está sendo declarado dentro do arquivo
####  Evitar declaração de vários objetos dentro do mesmo arquivo
Exemplos:
##### Não preferível
```swift
```

##### Correto
```swift
```
#### Todos os arquivos do tipo `Swift` devem terminar com a extensão `.swift`

### Comentários
Comentários no código são desencorajados, pois um código bem organizado e padronizado é o suficiente para servir de documentação.

### Copyright Statement
Não utilizar o `Copyright Statement` no cabeçalho do código, toda informação sobre histórico de modificação e criação pode ser verificada através do git.

### Frameworks
Não adicionar ao projeto frameworks e bibliotecas sem um motivo claro e sem discutir com o time. Frameworks e bibliotecas resolvem um problema relacionado ao tempo de desenvolvimento, porém adiciona uma complexidade excessiva ao código e pode gerar acoplamentos com mais facilidade. Optar sempre por fazer as coisas nativamente e de forma simples.

### Imports
Todos os `imports` devem ir no início do arquivo sem linhas em branco entre cada `import`. 

#### Não importar módulos redundantes
Exemplos:
##### Não preferível
```swift
import UIKit
import Foundation

class LoginViewController: UIViewController { }
```

##### Correto
```swift
import UIKit

class LoginViewController: UIViewController { }
```

#### Não importar módulos que não estejam sendo utilizados no arquivo
Exemplos:
##### Não preferível
```swift
import Foundation

struct User {
	let name: String
	let lastName: String
}
```

##### Correto
```swift
struct User {
	let name: String
	let lastName: String
}
```
