<script lang="ts">
  import { Input } from "$lib/components/ui/input/index.js";
  import * as Select from "$lib/components/ui/select/index.js";
  import { Checkbox } from "$lib/components/ui/checkbox/index.js";
  import { Label } from "$lib/components/ui/label/index.js";

  let formFactor = $state("");
  let ram = $state(0);
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
    <h2 class="text-xl">Operating Systems</h2>
    <div class="flex items-center space-x-2">
      <Checkbox id="windows" />
      <Label for="windows">Windows</Label>
    </div>
    <div class="flex items-center space-x-2">
      <Checkbox id="linux" />
      <Label for="linux">Linux</Label>
    </div>
    <div class="flex items-center space-x-2">
      <Checkbox id="chromeos" />
      <Label for="chromeos">ChromeOS</Label>
    </div>
    <div class="flex items-center space-x-2">
      <Checkbox id="bsd" />
      <Label for="bsd">BSD</Label>
    </div>
    <div class="flex items-center space-x-2">
      <Checkbox id="other" />
      <Label for="other">Other</Label>
    </div>
  </div>
</div>
