# GraphQL

## 🎓 J'ai compris et je peux expliquer

- la différence entre REST et GraphQL ✔️
- les besoins auxquels répond GraphQL ✔️
- la définition d'un schéma
- Query ✔️
- Mutation ✔️
- Subscription ✔️

## 💻 J'utilise

### Utilisation dans un projet ❌ / ✔️

```javascript
@Resolver(VerificationCode)
export class VerificationCodeResolver {
  @Mutation(() => Boolean)
  async generateNewVerificationCode(
    @Arg("userId") userId: number
  ): Promise<boolean> {
    try {
      const user = await User.findOneBy({ id: userId });
      if (!user) {
        throw new Error("Utilisateur non trouvé");
      }
      const verificationCodeLength = 8;
      const newCode = generateSecurityCode(verificationCodeLength);
      let verificationCode = await VerificationCode.findOneBy({
        user: { id: userId },
        type: typeCodeVerification,
      });
      if (verificationCode) {
        verificationCode.code = newCode;
        verificationCode.expirationDate = new Date(
          Date.now() + 24 * 60 * 60 * 1000
        );
        verificationCode.maximumTry = 0;
      } else {
        verificationCode = VerificationCode.create({
          user,
          code: newCode,
          type: typeCodeVerification,
          expirationDate: new Date(Date.now() + 24 * 60 * 60 * 1000),
          maximumTry: 0,
        });
      }

      await verificationCode.save();

      await sendVerificationEmail(user.id, user.email, newCode);

      return true;
    } catch (error) {
      return false;
    }
  }
}

  @Query(() => [Category])
  async allCategories(): Promise<Category[]> {
    const categories = await Category.find({ relations: { ads: true } });
    return categories;
  }

  @Query(() => Category, { nullable: true })
  async category(@Arg("id", () => ID) id: number): Promise<Category | null> {
    const category = await Category.findOne({
      where: { id: id },
      relations: { ads: true },
    });
    return category;
  }

  @Mutation(() => Category)
  async createCategory(
    @Arg("data", () => CategoryCreateInput) data: CategoryCreateInput
  ): Promise<Category> {
    const newCategory = new Category();
    Object.assign(newCategory, data);

    const errors = await validate(newCategory);
    if (errors.length === 0) {
      await newCategory.save();
      return newCategory;
    } else {
      throw new Error(`Error occured: ${JSON.stringify(errors)}`);
    }
  }

  @Mutation(() => Category, { nullable: true })
  async updateCategory(
    @Arg("id", () => ID) id: number,
    @Arg("data") data: CategoryUpdateInput
  ): Promise<Category | null> {
    const category = await Category.findOne({
      where: { id: id },
    });
    if (category) {
      Object.assign(category, data);

      const errors = await validate(category);
      if (errors.length === 0) {
        await category.save();
      } else {
        throw new Error(`Error occured: ${JSON.stringify(errors)}`);
      }
    }
    return category;
  }

```

### Utilisation en environement professionnel ❌

Description :

### Titre

### les limites de REST:

- Overfetching (on a tendance a récupérer plus d'informations que le client en demande)
- Multiplication des appels
- Typage

### Les besoins auquels répondent Graphql

- Exact-fetching

### Différence principales entre REST et GraphQL:

- Rest plusieurs points d'entrée // GraphQL un seul point d'entrée intelligent
- Graphql pas d'endpoints nommé comme les fichiers,le client fait sa demande parmis les méthodes proposé par le serveur

### GraphQL:

- Fortement Typé
- Type peuvent être scalaire (type primitifs) ou des objets avec champs
- relations définis dans les schémas
- Subscriptions = notifications en temps réels
- Resolvers (remplacent les controllers en REST) qui sont appellé pour répondre au mutation/queries

### Ressources externes (liens)
