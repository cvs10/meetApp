<script>
	import Header from './UI/Header.svelte';
    import MeetupItem from './Meetups/MeetupItem.svelte';

    const meetups = [
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
</script>

<style>
    #meetups{
        margin-top: 5rem;
    }
</style>

<Header />

<section id="meetups">
    {#each meetups as meetup}
    <MeetupItem 
    title={meetup.title} 
    subtitle={meetup.subtitle}
    adress={meetup.adress}
    description={meetup.description}
    imageUrl={meetup.imageUrl}
    email={meetup.contactEmail}/>
    {/each}
</section>

