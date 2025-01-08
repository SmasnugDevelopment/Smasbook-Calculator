<script lang="ts">
  import { Input } from "$lib/components/ui/input/index.js";
  import * as Select from "$lib/components/ui/select/index.js";
  import { Checkbox } from "$lib/components/ui/checkbox/index.js";
  import { Label } from "$lib/components/ui/label/index.js";

  let formFactor = $state("");
  let ram = $state(0);
  let screensize = $state(0);
  let touchscreen = $state(false);
  let windows = $state(false);
  let linux = $state(false);
  let chromeos = $state(false);
  let other = $state(false);
  let oscount = $derived(
    [windows, linux, chromeos, other].filter((os) => os).length
  );
</script>

<div class="w-screen h-screen flex flex-col justify-center items-center">
  <div class="w-96 max-w-full flex gap-3 flex-col">
    <h1 class="text-3xl">Smasbook Calculator</h1>
    <Select.Root bind:value={formFactor} type="single">
      <Select.Trigger>{formFactor || "Form factor"}</Select.Trigger>
      <Select.Content>
        <Select.Item value="Laptop">Laptop</Select.Item>
        <Select.Item value="PC">PC</Select.Item>
      </Select.Content>
    </Select.Root>
    <Input placeholder="GB of RAM" type="number" bind:value={ram} />
    <Input
      placeholder="Screen size in inches"
      type="number"
      bind:value={screensize}
    />
    <div class="flex items-center space-x-2">
      <Checkbox id="touchscreen" bind:checked={touchscreen} />
      <Label for="touchscreen">Touchscreen</Label>
    </div>
    <h2 class="text-xl">Operating Systems</h2>
    <div class="flex items-center space-x-2">
      <Checkbox id="windows" bind:checked={windows} />
      <Label for="windows">Windows</Label>
    </div>
    <div class="flex items-center space-x-2">
      <Checkbox id="linux" bind:checked={linux} />
      <Label for="linux">Linux</Label>
    </div>
    <div class="flex items-center space-x-2">
      <Checkbox id="chromeos" bind:checked={chromeos} />
      <Label for="chromeos">ChromeOS</Label>
    </div>
    <div class="flex items-center space-x-2">
      <Checkbox id="other" bind:checked={other} />
      <Label for="other">Other</Label>
    </div>
    {#if formFactor}
      <h2 class="text-xl">You have a:</h2>
      <span class="text-4xl">
        {#if formFactor === "PC"}Smasbox{:else}Smasbook{/if}
        {#if linux == true}Pro{/if}
        {#if oscount > 1}Plus{/if}
        {#if screensize >= 14}Max{/if}
        {#if ram >= 16}Ultra{/if}
        {#if oscount == 1 && chromeos}Lite{/if}
        {#if touchscreen}Touch{/if}
      </span>
    {/if}
  </div>
</div>
