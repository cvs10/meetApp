<script>
	import Header from './UI/Header.svelte';
    import MeetupGrid from './Meetups/MeetupGrid.svelte';
    import TextInput from "./UI/TextInput.svelte";
    import Button from "./UI/Button.svelte";
    import EditMeetup from "./Meetups/EditMeetup.svelte";

    


    let meetups = [
        {
            id: "m1",
            title: "30days Coding Bootcamp",
            subtitle: "Learn to code in 30 days",
            description: "Whole month of intensive coding",
            imageUrl: "https://picsum.photos/200/300",
            adress: 'Randomstraat 55, 6005 VX Heeze',
            email: 'random@gmail.com',
            isFavorite: false,
        },
        {
            id: "m2",
            title: "Code verification",
            subtitle: "Learn to verificate code",
            description: "Fast meetup about code verification",
            imageUrl: "https://picsum.photos/200/300",
            adress: 'Randomstraat 22, 5005 PP Budel',
            email: 'random2@gmail.com',
            isFavorite: false,
        }
    ];


    let editMode;
    
    function addMeetup(event){
        const newMeetup = {
            id: Math.random().toString(),
            title: event.detail.title,
            subtitle: event.detail.subtitle,
            description: event.detail.description,
            imageUrl: event.detail.imageUrl,
            email: event.detail.email,
            adress: event.detail.adress
        };
        meetups = [newMeetup, ...meetups];
        editMode = null;
    };

        function toggleFavorite(event){
            const id = event.detail;
            const updatedMeetup = { ...meetups.find(m => m.id === id) };
            updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
            const meetupIndex = meetups.findIndex(m => m.id === id);
            const updatedMeetups = [...meetups];
            updatedMeetups[meetupIndex] = updatedMeetup;
            meetups = updatedMeetups;
        }
</script>

<style>
    main{
        margin-top: 5rem;
    }

    .meetup_btn {
        margin: 1rem;
    }
</style>

<Header />
    
<main>
    <div class="meetup_btn">
    <Button on:click="{() => (editMode = 'add')}">New Meetup</Button>
    </div>
        {#if editMode === 'add'}
    
    <EditMeetup on:save="{addMeetup}"/>
        {/if}
    <MeetupGrid meetups={meetups} on:toggle-favorite={toggleFavorite}/>
</main>

