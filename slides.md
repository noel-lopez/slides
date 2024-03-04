---
theme: default
colorScheme: dark
---

# Mars Rover

Test-Driven development Kata

Noel López, David Huertas, Unai Mengual

---

# First iterations
<div grid="~ cols-2 gap-2">
<div>
<h4>Testing</h4>
````md magic-move

```ts

```

```ts
it('should face West when given "L" command', () => {
  const rover = new Rover()
  expect(rover.execute('L')).toBe('0:0:W')
})
```

````
</div>
<div>
<h4>Code</h4>
````md magic-move

```ts

```

```ts
export class Rover {
  execute(commands: string): string {
    return '0:0:W'
  }
}
```

````
</div>
</div>

---

# First iterations

<div grid="~ cols-2 gap-2">
<div>
<h4>Testing</h4>
````md magic-move

```ts
it('should face West when given "L" command', () => {
  const rover = new Rover()
  expect(rover.execute('L')).toBe('0:0:W')
})
```

```ts
it('should face West when given "L" command', () => {
  const rover = new Rover()
  expect(rover.execute('L')).toBe('0:0:W')
})

it('should face South when given "LL" command', () => {
  const rover = new Rover()
  expect(rover.execute('LL')).toBe('0:0:S')
})
```

````
</div>

<div>
<h4>Code</h4>
````md magic-move

```ts
export class Rover {
  execute(commands: string): string {
    return '0:0:W'
  }
}

```

```ts
export class Rover {
  execute(commands: string): string {
    if (commands === 'L') {
      return '0:0:W'
    }
    return '0:0:S'
  }
}

```

````

</div>
</div>

---

# First iterations

<div grid="~ cols-2 gap-2">
<div>
<h4>Testing</h4>
````md magic-move

```ts
it('should face West when given "L" command', () => {
  const rover = new Rover()
  expect(rover.execute('L')).toBe('0:0:W')
})

it('should face South when given "LL" command', () => {
  const rover = new Rover()
  expect(rover.execute('LL')).toBe('0:0:S')
})
```

```ts
it('should face West when given "L" command', () => {
  const rover = new Rover()
  expect(rover.execute('L')).toBe('0:0:W')
})

it('should face South when given "LL" command', () => {
  const rover = new Rover()
  expect(rover.execute('LL')).toBe('0:0:S')
})

it('should face East when given "LLL" command', () => {
  const rover = new Rover()
  expect(rover.execute('LLL')).toBe('0:0:E')
})
```

````
</div>
<div>
<h4>Code</h4>
````md magic-move

```ts
export class Rover {
  execute(commands: string): string {
    if (commands === 'L') {
      return '0:0:W'
    }
    return '0:0:S'
  }
}
```

```ts
export class Rover {
  execute(commands: string): string {
    if (commands === 'L') {
      return '0:0:W'
    }
    if (commands === 'LL') {
      return '0:0:S'
    }
    return '0:0:E'
  }
}
```

````
</div>
</div>

---

# First iterations <span v-click="3">- <span class="text-red-400">REFACTOR!!!</span></span>

<div grid="~ cols-2 gap-2">
<div>

<h4>Testing</h4>
````md magic-move

```ts
it('should face West when given "L" command', () => {
  const rover = new Rover()
  expect(rover.execute('L')).toBe('0:0:W')
})

it('should face South when given "LL" command', () => {
  const rover = new Rover()
  expect(rover.execute('LL')).toBe('0:0:S')
})

it('should face East when given "LLL" command', () => {
  const rover = new Rover()
  expect(rover.execute('LLL')).toBe('0:0:E')
})
```

```ts
it('should face West when given "L" command', () => {
  const rover = new Rover()
  expect(rover.execute('L')).toBe('0:0:W')
})

it('should face South when given "LL" command', () => {
  const rover = new Rover()
  expect(rover.execute('LL')).toBe('0:0:S')
})

it('should face East when given "LLL" command', () => {
  const rover = new Rover()
  expect(rover.execute('LLL')).toBe('0:0:E')
})

it('should face North when given "LLLL" command', () => {
  const rover = new Rover()
  expect(rover.execute('LLLL')).toBe('0:0:N')
})
```

````
</div>

<div>

<h4>Code</h4>
````md magic-move

```ts
export class Rover {
  execute(commands: string): string {
    if (commands === 'L') {
      return '0:0:W'
    }
    if (commands === 'LL') {
      return '0:0:S'
    }
    return '0:0:E'
  }
}
```

```ts
export class Rover {
  execute(commands: string): string {
    if (commands === 'L') {
      return '0:0:W'
    }
    if (commands === 'LL') {
      return '0:0:S'
    }
    if (commands === 'LLL') {
      return '0:0:E'
    }
    return '0:0:N'
  }
}
```

```ts
export class Rover {
  execute(commands: string): string {
    if (commands === 'L') {
      return '0:0:W'
    }
    if (commands === 'LL') {
      return '0:0:S'
    }
    if (commands === 'LLL') {
      return '0:0:E'
    }
    return '0:0:N'
  }
}
```

```ts
export class Rover {

  private orientation: string = 'N'

  execute(commands: string): string {
    if (commands === 'L') {
      return '0:0:W'
    }
    if (commands === 'LL') {
      return '0:0:S'
    }
    if (commands === 'LLL') {
      return '0:0:E'
    }
    return '0:0:N'
  }
}
```

```ts
export class Rover {

  private orientation: string = 'N'

  execute(commands: string): string {
    const splittedCommands = commands.split('')
  }
}
```

```ts
export class Rover {

  private orientation: string = 'N'

  execute(commands: string): string {
    const splittedCommands = commands.split('')
    for (const command of splittedCommands) {
      
    }
  }
}
```

```ts
export class Rover {

  private orientation: string = 'N'

  execute(commands: string): string {
    const splittedCommands = commands.split('')
    for (const command of splittedCommands) {
      this.turnLeft()
    }
  }

  private turnLeft() {
    /* ... */
  }
}
```

```ts
export class Rover {

  private orientation: string = 'N'

  execute(commands: string): string {
    const splittedCommands = commands.split('')
    for (const command of splittedCommands) {
      this.turnLeft()
    }
    return `0:0:${this.orientation}`
  }

  private turnLeft() {
    /* ... */
  }
}
```

```ts
export class Rover {

  private orientation: string = 'N'

  execute(commands: string): string {
    const splittedCommands = commands.split('')
    for (const command of splittedCommands) {
      if (command === 'L') { // <-- Proximamente
        this.turnLeft()
      }
    }
    return `0:0:${this.orientation}`
  }

  private turnLeft() {
    /* ... */
  }
}
```

```ts
export class Rover {

  private orientation: string = 'N'

  execute(commands: string): string {
    /* ... */
  }

  private turnLeft() {
    /* ... */
  }
}
```

```ts
export class Rover {

  private orientation: string = 'N'

  execute(commands: string): string {
    /* ... */
  }

  private turnLeft() {
    if (this.orientation === 'N') {
      this.orientation = 'W'
    } else if (this.orientation === 'W') {
      this.orientation = 'S'
    } else if (this.orientation === 'S') {
      this.orientation = 'E'
    } else if (this.orientation === 'E') {
      this.orientation = 'N'
    }
  }
}
```

````

</div>

</div>

---
layout: center
---

# SUFICIENTE!!
<h2 v-click>Creo que ya lo habeis entendido, pasemos al código resultante de estas primeras iteraciones.</h2>

---

# Código resultante

```ts
export default class Rover {

  private orientation = "N"
  private x = 0
  private y = 0

  public execute(commands: string): string {
    /* EJECUTA LOS METODOS PRIVADOS DEPENDIENDO DE LOS COMANDOS RECIBIDOS */
    /* DEVUELVE LA POSICION Y ORIENTACION DEL ROVER */
  }

  private rotateLeft(): void {
    /* CAMBIA LA ORIENTACION DEL ROVER HACIA LA IZQUIERDA */
  }

  private rotateRight(): void {
    /* CAMBIA LA ORIENTACION DEL ROVER HACIA LA DERECHA */
  }

  private moveForward(): void {
    /* CAMBIA LA POSICION (X, Y) DEL ROVER HACIA ADELANTE DEPENDIENDO DE SU ORIENTACION */
  }
}
```

---

# Código resultante - <span class="text-purple-300">execute()</span>

```ts
public execute(commands: string): string {
  const splittedCommands = commands.split('')
  for (const command of splittedCommands) {
    if (command === "L") {
      this.rotateLeft()
    }
    if (command === "R") {
      this.rotateRight()
    }
    if (command === "M") {
      this.moveForward()
    }
  }
  return `${this.x}:${this.y}:${this.orientation}`
}
```

---

# Código resultante - <span class="text-purple-300">rotateLeft()</span>

```ts
private rotateLeft(): void {
  if (this.orientation === "N") {
    this.orientation = "W"
  } else if (this.orientation === "W") {
    this.orientation = "S"
  } else if (this.orientation === "S") {
    this.orientation = "E"
  } else {
    this.orientation = "N"
  }
}
```

---

# Código resultante - <span class="text-purple-300">rotateRight()</span>

```ts
private rotateRight(): void {
  if (this.orientation === "N") {
    this.orientation = "E"
  } else if (this.orientation === "E") {
    this.orientation = "S"
  } else if (this.orientation === "S") {
    this.orientation = "W"
  } else {
    this.orientation = "N"
  }
}
```

---

# Código resultante - <span class="text-purple-300">moveForward()</span>

```ts
private moveForward(): void {
  if (this.orientation === "N") {
    this.y++
  } else if (this.orientation === "E") {
    this.x++
  } else if (this.orientation === "S") {
    this.y--
  } else {
    this.x--
  }
}
```

---

# Refactor - Orientation

````md magic-move

```ts
export default class Rover {
  private orientation = "N"
  private x = 0
  private y = 0
}
```

```ts
interface Orientation {
  rotateLeft(): Orientation
  rotateRight(): Orientation
  moveForward(): { x: number, y: number }
}

export default class Rover {
  private orientation = "N"
  private x = 0
  private y = 0
}
```

```ts
interface Orientation {
  rotateLeft(): Orientation
  rotateRight(): Orientation
  moveForward(): { x: number, y: number }
}

class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
}

export default class Rover {
  private orientation = "N"
  private x = 0
  private y = 0
}
```

```ts
interface Orientation {
  rotateLeft(): Orientation
  rotateRight(): Orientation
  moveForward(): { x: number, y: number }
}

class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0
}
```

```ts
interface Orientation {
  rotateLeft(): Orientation
  rotateRight(): Orientation
  moveForward(): { x: number, y: number }
}

class East implements Orientation {
  rotateLeft(): Orientation {
    return new North()
  }
  rotateRight(): Orientation {
    return new South()
  }
  moveForward() {
    return { x: 1, y: 0 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0
}
```

```ts
interface Orientation {
  rotateLeft(): Orientation
  rotateRight(): Orientation
  moveForward(): { x: number, y: number }
}

class South implements Orientation {
  rotateLeft(): Orientation {
    return new East()
  }
  rotateRight(): Orientation {
    return new West()
  }
  moveForward() {
    return { x: 0, y: -1 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0
}
```

```ts
interface Orientation {
  rotateLeft(): Orientation
  rotateRight(): Orientation
  moveForward(): { x: number, y: number }
}

class West implements Orientation {
  rotateLeft(): Orientation {
    return new South()
  }
  rotateRight(): Orientation {
    return new North()
  }
  moveForward() {
    return { x: -1, y: 0 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0
}
```

```ts
interface Orientation {
  rotateLeft(): Orientation
  rotateRight(): Orientation
  moveForward(): { x: number, y: number }
}

class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0
}
```

```ts
class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0
}
```

```ts
class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0

  private rotateLeft(): void {
    if (this.orientation === "N") {
      this.orientation = "W"
    } else if (this.orientation === "W") {
      this.orientation = "S"
    } else if (this.orientation === "S") {
      this.orientation = "E"
    } else {
      this.orientation = "N"
    }
  }
}
```

```ts
class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0

  private rotateLeft(): void {
    
  }
}
```

```ts
class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0

  private rotateLeft(): void {
    this.orientation = this.orientation.rotateLeft()
  }
}
```

```ts
class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0

  private rotateLeft(): void {
    this.orientation = this.orientation.rotateLeft()
  }

  private rotateRight(): void {
    this.orientation = this.orientation.rotateRight()
  }
}
```

```ts
class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0

  
}
```

```ts
class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0

  private moveForward(): void {
    const { x, y } = this.orientation.moveForward()
    this.x += x
    this.y += y
  }
}
```

```ts
class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0


}
```

```ts
class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0

  public execute(commands: string): string {
    /* EXECUTE COMMANDS */
    return `${this.x}:${this.y}:${this.orientation}`
  }
}
```

```ts
class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
  toString() {
    return "N"
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0

  public execute(commands: string): string {
    /* EXECUTE COMMANDS */
    return `${this.x}:${this.y}:${this.orientation}`
  }
}
```

```ts
class North implements Orientation {
  rotateLeft(): Orientation {
    return new West()
  }
  rotateRight(): Orientation {
    return new East()
  }
  moveForward() {
    return { x: 0, y: 1 }
  }
  toString() {
    return "N"
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0

  public execute(commands: string): string {
    /* EXECUTE COMMANDS */
    return `${this.x}:${this.y}:${this.orientation.toString()}`
  }
}
```


````