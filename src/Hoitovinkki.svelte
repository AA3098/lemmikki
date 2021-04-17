<script>
  export let nakyvyysAika;
  const vinkit = [
    'Remember to feed your cat overlords daily',
    'Pet your lord and masters when they want attention',
    'Be a good little slave and brush your masters coat often',
    'Catnip, ever heard of it?',
  ];
  let i = 0;
  setInterval(function () {
    if (i === vinkit.length - 1) {
      i = 0;
    } else {
      i++;
    }
  }, nakyvyysAika);
</script>

<h2>
  {vinkit[i]}
</h2>
