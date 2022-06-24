<script>
  import Header from './components/Header.svelte';
  import Tab from './components/Tab.svelte';
  import Tabs from './components/Tabs.svelte';
  import TabList from './components/TabList.svelte';
  import TabPanel from './components/TabPanel.svelte';
  import Cripta from './components/Cripta.svelte';
import Libreria from './components/Libreria.svelte';
</script>

<main>
  <Header />
  <Tabs>
    <TabList>
      <Tab>Cripta</Tab>
      <Tab>Librería</Tab>
    </TabList>
    <TabPanel>
      <Cripta />
    </TabPanel>
    <TabPanel>
      <Libreria />
    </TabPanel>
  </Tabs>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }
  :global(body) {
    padding: 0;
    margin: 0;
  }
  main {
    text-align: center;
    padding: 0;
    margin: 0;
    background-color: #d3c265;
    height: 100%;
  }

</style>
