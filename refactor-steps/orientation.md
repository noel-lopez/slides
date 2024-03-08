
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
    // wrap around the grid
    this.x = (this.x + 10) % 10
    this.y = (this.y + 10) % 10
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

````