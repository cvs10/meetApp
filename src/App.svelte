<script>
	import Header from './UI/Header.svelte';
    import MeetupGrid from './Meetups/MeetupGrid.svelte';
    import TextInput from "./UI/TextInput.svelte";

    let title="";
    let subtitle="";
    let adress="";
    let email="";
    let description="";
    let imageUrl="";


    let meetups = [
        {
            id: "m1",
            title: "30days Coding Bootcamp",
            subtitle: "Learn to code in 30 days",
            description: "Whole month of intensive coding",
            imageUrl: "https://picsum.photos/200/300",
            adress: 'Randomstraat 55, 6005 VX Heeze',
            contactEmail: 'random@gmail.com'
        },
        {
            id: "m2",
            title: "Code verification",
            subtitle: "Learn to verificate code",
            description: "Fast meetup about code verification",
            imageUrl: "https://picsum.photos/200/300",
            adress: 'Randomstraat 22, 5005 PP Budel',
            contactEmail: 'random2@gmail.com'
        }
    ];
    
    function addMeetup(){
        const newMeetup = {
            id: Math.random().toString(),
            title: title,
            subtitle: subtitle,
            description: description,
            imageUrl: imageUrl,
            contactEmail: email,
            adress: adress
        }
        meetups = [newMeetup,...meetups]
    };
</script>

<style>
    form {
        margin-top: 5rem;
    }
    main{
        margin-top: 5rem;
    }

    form{
        width: 30rem;
        max-width: 90%;
        margin: auto;
        margin-top: 5rem;
    }
</style>

<Header />
    <form on:submit|preventDefault={addMeetup}>
        <TextInput id="title" label="Title" type="text" value={title} on:input={event => (title = event.target.value)} />
        <TextInput id="subtitle" label="Subtitle" type="text" value={subtitle} on:input={event => (subtitle = event.target.value)} />
        <TextInput id="adress" label="Adress" type="text" value={adress} on:input={event => (adress = event.target.value)} />
        <TextInput id="imageUrl" label="Image URL" type="text" value={imageUrl} on:input={event => (imageUrl = event.target.value)} />
        <TextInput id="email" label="Email" type="email" value={email} on:input={event => (email = event.target.value)} />
        <TextInput id="description" label="Description" controlType="textarea" value={description} on:input={event => (description = event.target.value)} />



        <button type="submit">Save</button>
    </form>
<main>
    <MeetupGrid meetups={meetups}/>
</main>

