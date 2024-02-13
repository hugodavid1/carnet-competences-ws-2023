# TypeScript

## 🎓 J'ai compris et je peux expliquer

- l'intéret de TypeScript dans l'IDE ✔️
- les types de bases ✔️
- comment et pourquoi étendre une interface ✔️
- les classes et les decorators ✔️

## 💻 J'utilise

### Un exemple dans un pojet ✔️

```javascript
export type AdType = {
id: number;
link: string;
imgUrl: string;
title: string;
price: number;
createdAt?: string;
description?: string;
category?: CategoryType | null;
};

export type AdCardProps = AdType & {
onDelete?: () => void;
};

const [error, setError] = useState<"title" | "price">();
const [title, setTitle] = useState<string>("");
const [description, setDescription] = useState<string>("");
const [imgUrl, setImgUrl] = useState<string>("");
const [price, setPrice] = useState<number>(0);
const [categoryId, setCategoryId] = useState<null | number>(null);
const [tagsId, setTagsId] = useState<null | number>(null);
const {
data: dataCategory,
error: errorCategory,
loading: loadingCategory,
} = useQuery<{ allCategories: CategoryType[] }>(queryAllCategories);
```

### Titre

[- lien](https://www.typescriptlang.org/docs/handbook/2/objects.html)
[- lien](https://ts.chibicode.com/todo/)

```

```
