**Zod React Hook Form**

---

**Introduction:**

Zod React Hook Form is a library that integrates Zod schema validation with React Hook Form, providing a seamless experience for validating forms in React applications.

---

**Installation:**

You can install Zod React Hook Form via npm or yarn:

```bash
npm install zod-react-hook-form
```

## Usage

```bash
import { useForm } from 'react-hook-form';
import { zodResolver } from 'zod-react-hook-form';
import { z } from 'zod';

# Define your Zod schema
const schema = z.object({
  email: z.string().email(),
  password: z.string().min(6),
});

# Use Zod resolver with useForm
const { register, handleSubmit, formState: { errors } } = useForm({
  resolver: zodResolver(schema)
});

# Your form component
function MyForm() {
  const onSubmit = (data) => console.log(data);

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register("email")} />
      {errors.email && <span>{errors.email.message}</span>}

      <input type="password" {...register("password")} />
      {errors.password && <span>{errors.password.message}</span>}

      <button type="submit">Submit</button>
    </form>
  );
}

```


