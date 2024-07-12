### 1. **Single Responsibility Principle (SRP)**

Cada classe deve ter uma única responsabilidade ou razão para mudar. Em outras palavras, uma classe deve fazer apenas uma coisa.

**Exemplo:**

javascript

Copy code
```javascript
// Violando SRP
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }

  save() {
    // Lógica para salvar usuário no banco de dados
  }

  sendEmail(message) {
    // Lógica para enviar email para o usuário
  }
}

// Seguindo SRP
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }
}

class UserRepository {
  save(user) {
    // Lógica para salvar usuário no banco de dados
  }
}

class EmailService {
  sendEmail(user, message) {
    // Lógica para enviar email para o usuário
  }
}

```

### 2. **Open/Closed Principle (OCP)**

As classes devem estar abertas para extensão, mas fechadas para modificação. Isso significa que devemos ser capazes de adicionar novos comportamentos a uma classe sem alterar seu código existente.

**Exemplo:**

```javascript
// Violando OCP
class Payment {
  pay(type) {
    if (type === 'credit') {
      // Lógica para pagamento com cartão de crédito
    } else if (type === 'paypal') {
      // Lógica para pagamento com PayPal
    }
  }
}

// Seguindo OCP
class Payment {
  pay(paymentMethod) {
    paymentMethod.processPayment();
  }
}

class CreditCardPayment {
  processPayment() {
    // Lógica para pagamento com cartão de crédito
  }
}

class PayPalPayment {
  processPayment() {
    // Lógica para pagamento com PayPal
  }
}

```

### 3. **Liskov Substitution Principle (LSP)**

Subtipos devem ser substituíveis por seus tipos base sem alterar a funcionalidade do programa.

**Exemplo:**

```javascript
// Violando LSP
class Bird {
  fly() {
    // Lógica para voar
  }
}

class Ostrich extends Bird {
  fly() {
    throw new Error("Ostriches can't fly");
  }
}

// Seguindo LSP
class Bird {
  // Classe base vazia ou métodos comuns a todas as aves
}

class FlyingBird extends Bird {
  fly() {
    // Lógica para voar
  }
}

class Ostrich extends Bird {
  // Sem método fly, pois avestruzes não voam
}

```

### 4. **Interface Segregation Principle (ISP)**

Muitas interfaces específicas são melhores do que uma única interface geral. As classes não devem ser forçadas a implementar interfaces que elas não utilizam.

**Exemplo:**

```javascript
// Violando ISP
class Worker {
  work() {
    // Lógica para trabalhar
  }

  eat() {
    // Lógica para comer
  }
}

// Seguindo ISP
class Workable {
  work() {
    // Lógica para trabalhar
  }
}

class Eatable {
  eat() {
    // Lógica para comer
  }
}

class Worker implements Workable, Eatable {
  work() {
    // Lógica para trabalhar
  }

  eat() {
    // Lógica para comer
  }
}
```

### 5. **Dependency Inversion Principle (DIP)**

Dependa de abstrações, não de implementações. Os módulos de alto nível não devem depender de módulos de baixo nível. Ambos devem depender de abstrações.

**Exemplo:**

```javascript
// Violando DIP
class User {
  constructor() {
    this.emailService = new EmailService();
  }

  notify(message) {
    this.emailService.sendEmail(this, message);
  }
}

// Seguindo DIP
class User {
  constructor(emailService) {
    this.emailService = emailService;
  }

  notify(message) {
    this.emailService.sendEmail(this, message);
  }
}

class EmailService {
  sendEmail(user, message) {
    // Lógica para enviar email
  }
}

// Inversão da dependência
const emailService = new EmailService();
const user = new User(emailService);
```

