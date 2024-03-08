
# Refactor - Position

````md magic-move

```ts
export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0
}
```

```ts
class Position {
  private x = 0
  private y = 0
}

export default class Rover {
  private orientation: Orientation = new North()
  private x = 0
  private y = 0
}
```

```ts
class Position {
  private x = 0
  private y = 0
}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
}
```

```ts
class Position {
  private x = 0
  private y = 0
}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
  
  public execute(commands: string) {
    /* EXECUTE COMMANDS */
    return `${this.x}:${this.y}:${this.orientation}`
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0

  public toString() {
    return `${this.x}:${this.y}`
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
  
  public execute(commands: string) {
    /* EXECUTE COMMANDS */
    return `${this.x}:${this.y}:${this.orientation}`
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0

  public toString() {
    return `${this.x}:${this.y}`
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
  
  public execute(commands: string) {
    /* EXECUTE COMMANDS */
    return `${this.position}:${this.orientation}`
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0

  public toString() {
    return `${this.x}:${this.y}`
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
  
  
}
```

```ts
class Position {
  private x = 0
  private y = 0

  public toString() {
    return `${this.x}:${this.y}`
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
  
  private moveForward(): void {
    const { x, y } = this.orientation.moveForward()
    this.x += x
    this.y += y
    // wrap around the grid
    this.x = (this.x + 10) % 10
    this.y = (this.y + 10) % 10
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0

  public toString() {
    return `${this.x}:${this.y}`
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
  
  private moveForward(): void {
    const { x, y } = this.orientation.moveForward()
    
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0

  public toString() {
    return `${this.x}:${this.y}`
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
  
  private moveForward(): void {
    const { x, y } = this.orientation.moveForward()
    this.position.move({ x, y })
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0


}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
  
  private moveForward(): void {
    const { x, y } = this.orientation.moveForward()
    this.position.move({ x, y })
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0

  public move({ x, y }: { x: number, y: number }) {

  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
  
  private moveForward(): void {
    const { x, y } = this.orientation.moveForward()
    this.position.move({ x, y })
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0

  public move({ x, y }: { x: number, y: number }) {
    this.x += x
    this.y += y
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
  
  private moveForward(): void {
    const { x, y } = this.orientation.moveForward()
    this.position.move({ x, y })
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0

  public move({ x, y }: { x: number, y: number }) {
    this.x += x
    this.y += y
    // wrap around the grid
    this.x = (this.x + 10) % 10
    this.y = (this.y + 10) % 10
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
  
  private moveForward(): void {
    const { x, y } = this.orientation.moveForward()
    this.position.move({ x, y })
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0

  public move({ x, y }: { x: number, y: number }) {
    this.x += x
    this.y += y
    // wrap around the grid
    this.x = (this.x + 10) % 10
    this.y = (this.y + 10) % 10
  }

  private wrapAroundGrid() {
    this.x = (this.x + 10) % 10
    this.y = (this.y + 10) % 10
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
  
  private moveForward(): void {
    const { x, y } = this.orientation.moveForward()
    this.position.move({ x, y })
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0

  public move({ x, y }: { x: number, y: number }) {
    this.x += x
    this.y += y
    this.wrapAroundGrid()
  }

  private wrapAroundGrid() {
    this.x = (this.x + 10) % 10
    this.y = (this.y + 10) % 10
  }
}

export default class Rover {
  private orientation: Orientation = new North()
  private position = new Position()
  
  private moveForward(): void {
    const { x, y } = this.orientation.moveForward()
    this.position.move({ x, y })
  }
}
```

````