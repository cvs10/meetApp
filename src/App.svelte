<script>
	import Header from './UI/Header.svelte';
    import MeetupGrid from './Meetups/MeetupGrid.svelte';

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
</style>

<Header />
    <form on:submit|preventDefault={addMeetup}>
        <div class="form-control">
            <label for="title">Title</label>
            <input type="text" id="title" bind:value={title}>
        </div>
        <div class="form-control">
            <label for="subtitle">Subtitle</label>
            <input type="text" id="subtitle" bind:value={subtitle}>
        </div>
        <div class="form-control">
            <label for="adress">Adress</label>
            <input type="text" id="adress" bind:value={adress}>
        </div>
        <div class="form-control">
            <label for="imageUrl">Image Url</label>
            <input type="text" id="imageUrl" bind:value={imageUrl}>
        </div>
        <div class="form-control">
            <label for="email">Email</label>
            <input type="email" id="email" bind:value={email}>
        </div>
        <div class="form-control">
            <label for="description">Description</label>
            <textarea id="description" cols="30" rows="5" bind:value={description}></textarea>
        </div>
        <button type="submit">Save</button>
    </form>
<main>
    <MeetupGrid meetups={meetups}/>
</main>

