<script>
  import Header from './UI/Header.svelte';
  import MeetupGrid from './Meetups/MeetupGrid.svelte'
  import TextInput from './UI/TextInput.svelte'

  let title = '';
  let subtitle = '';
  let address = '';
  let email = '';
  let description = '';
  let imageUrl = '';

  let meetups = [
    {
      id: 'm1',
      title: 'Coding Bootcamp',
      subtitle: 'Learn to code in 2 hours',
      description: 'In this meetup, we will have some experts that teach you how to code!',
      imageUrl: 'https://via.placeholder.com/150',
      address: '27th Nerd Road, 32523 New York',
      contactEmail: 'code@test.com'
    },
    {
      id: 'm2',
      title: 'Swim Together',
      subtitle: 'Let\'s go for some swimming',
      description: 'We will simply some rounds!',
      imageUrl: 'https://via.placeholder.com/150',
      address: '27th Nerd Road, 32523 New York',
      contactEmail: 'swim@test.com'
    }
  ]

  function addMeetup(){
    const newMeetup = {
      id: Math.random().toString(),
      contactEmail: email,
      imageUrl: imageUrl || 'https://via.placeholder.com/150',
      title,
      subtitle,
      description,
      address,
    }

    meetups = [
      ...meetups,
      newMeetup,
    ]
  }
</script>

<style>
  main {
    margin-top: 5rem;
  }

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>

<Header />

<main>
  <form on:submit|preventDefault="{addMeetup}">
    <TextInput
      id="title"
      label="Title"
      value="{title}"
      on:input="{event => (title = event.target.value)}"
    />
    <TextInput
      id="subtitle"
      label="Subtitle"
      value="{subtitle}"
      on:input="{event => (subtitle = event.target.value)}"
    />
    <TextInput
      id="address"
      label="Address"
      value="{address}"
      on:input="{event => (address = event.target.value)}"
    />
    <TextInput
      id="title"
      label="Title"
      value="{title}"
      on:input="{event => (title = event.target.value)}"
    />
    <TextInput
      id="imageUrl"
      label="ImageUrl"
      value="{imageUrl}"
      on:input="{event => (imageUrl = event.target.value)}"
    />
    <TextInput
      id="email"
      label="E-Mail"
      value="{email}"
      on:input="{event => (email = event.target.value)}"
    />
    <TextInput
      id="description"
      controlType="textarea"
      rows="3"
      label="Description"
      value="{description}"
      on:input="{event => (description = event.target.value)}"
    />
    <button type="submit">Save</button>
  </form>
  <MeetupGrid meetups="{meetups}"/>
</main>
