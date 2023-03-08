<script lang="ts">
  let name = 'test';
  let number: number = 10;
  let src =
    'https://img3.akspic.ru/previews/7/4/2/8/6/168247/168247-kosti_3d-igra_v_kosti_3d-azartnaya_igra-pitevaya_igra-kazino-500x.jpg';
  let altText = 'test';
  let htmlString = '<b>test</b>';

  let pos = {
    x: 0,
    y: 0
  };
  let input = '';

  const incrementNumber = () => {
    number++;
  };
  const decrementNumber = () => {
    number--;
  };
  const mousemoveHandler = (evt: MouseEvent) => {
    pos.x = evt.x;
    pos.y = evt.y;
  };
  const inputHandler = (evt: Event) => {
    const target = evt.target as HTMLInputElement;

    if (!target) return;

    input = target.value;
  };
</script>

<svelte:head>
  <title>Home</title>
  <meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
  <h1>Hello {name.toUpperCase()}!</h1>
  <div>{number}</div>
  <button type="button" on:click={decrementNumber}>Уменьшить число</button>
  <button type="button" on:click={incrementNumber}>Увеличить число</button>
  <div>
    <img {src} alt={altText} />
  </div>
  <div>htmlString - {htmlString}</div>
  <div>htmlString - {@html htmlString}</div>

  <div class="playground" on:mousemove={mousemoveHandler}>
    <h2>X: {pos.x}, Y: {pos.y}</h2>
  </div>

  <form on:submit={() => console.log('Submit:', input)}>
    <input type="text" on:input={inputHandler} />
    <button type="submit">Submit</button>
  </form>
</section>

<style lang="scss">
  img {
    width: 150px;
    margin-bottom: 10px;
  }

  .playground {
    width: 300px;
    height: 200px;
    border: 1px solid #000;
    margin: 16px 0;
  }
</style>
