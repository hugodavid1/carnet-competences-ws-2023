# TypeScript

## 🎓 J'ai compris et je peux expliquer

- l'intéret de TypeScript dans l'IDE ✔️
- les types de bases ✔️
- comment et pourquoi étendre une interface ✔️
- les classes et les decorators ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

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

### Utilisation dans un projet ❌ / ✔️

[lien github](...)

Description :

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
