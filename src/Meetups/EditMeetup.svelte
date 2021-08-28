<script>
    import { createEventDispatcher } from "svelte";
    import TextInput from "../UI/TextInput.svelte";
    import Button from "../UI/Button.svelte";

    let title="";
    let subtitle="";
    let adress="";
    let email="";
    let description="";
    let imageUrl="";

    const dispatch = createEventDispatcher();

    function submitForm() {
        dispatch('save', {
            title: title,
            subtitle: subtitle,
            adress: adress,
            email: email,
            description: description,
            imageUrl: imageUrl

        });
    }
</script>

<style>
    form{
        width: 30rem;
        max-width: 90%;
        margin: auto;
        margin-top: 5rem;
    }
</style>


<form on:submit|preventDefault={submitForm}>
    <TextInput id="title" label="Title" type="text" value={title} on:input={event => (title = event.target.value)} />
    <TextInput id="subtitle" label="Subtitle" type="text" value={subtitle} on:input={event => (subtitle = event.target.value)} />
    <TextInput id="adress" label="Adress" type="text" value={adress} on:input={event => (adress = event.target.value)} />
    <TextInput id="imageUrl" label="Image URL" type="text" value={imageUrl} on:input={event => (imageUrl = event.target.value)} />
    <TextInput id="email" label="Email" type="email" value={email} on:input={event => (email = event.target.value)} />
    <TextInput id="description" label="Description" controlType="textarea" value={description} on:input={event => (description = event.target.value)} />



    <Button type="submit">Save</Button>
</form>