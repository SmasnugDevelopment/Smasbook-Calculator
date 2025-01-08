<script lang="ts">
  import { Input } from "$lib/components/ui/input/index.js";
  import * as Select from "$lib/components/ui/select/index.js";

  let formFactor = $state("");
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
    <Input placeholder="GB of RAM" type="number" />
  </div>
</div>
