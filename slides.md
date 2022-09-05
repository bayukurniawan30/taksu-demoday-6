---
theme: purplin
class: 'text-center'
highlighter: prism
lineNumbers: true
info: |
  ## Taksu Demo Day 6
drawings:
  persist: false
---

## RxJs Error Handling

Taksu Demo Day #6

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Next <carbon:arrow-right class="inline"/>
  </span>
</div>

<BarBottom  title="Taksu Demo Day #6">
  <Item text="Bayu Kurniawan">
    <carbon:user-avatar />
  </Item>
</BarBottom>

<!--
Comment here
-->

---

# What?

<div v-click class="text-2xl text-white mt-20 leading-5">

Error handling refers to the routines in a program that respond to abnormal input or conditions.

</div>

<BarBottom  title="Taksu Demo Day #6">
  <Item text="Bayu Kurniawan">
    <carbon:user-avatar />
  </Item>
</BarBottom>

---

# Why?

<div v-click class="text-2xl text-white mt-20">For user</div>
<div v-click class="text-2xl text-white mt-3">- Improve UX</div>
<div v-click class="text-2xl text-white mt-3">- Help the user to determine the next action</div>

<div v-click class="text-2xl text-white mt-10">For developer</div>
<div v-click class="text-2xl text-white mt-3">- To know what happened in the system</div>
<div v-click class="text-2xl text-white mt-3">- To see what's the response from API</div>


<BarBottom  title="Taksu Demo Day #6">
  <Item text="Bayu Kurniawan">
    <carbon:user-avatar />
  </Item>
</BarBottom>

---

# When?

<div v-click class="text-2xl text-white mt-20 leading-5">

In every action in the system

</div>

<div v-click class="text-2xl text-white mt-10">- When user create, update, or delete data</div>


<BarBottom  title="Taksu Demo Day #6">
  <Item text="Bayu Kurniawan">
    <carbon:user-avatar />
  </Item>
</BarBottom>

---

# How?

<div v-click class="text-2xl text-white mt-20">Front End</div>
<div v-click class="text-2xl text-white mt-3">- RxJs (HTTP Request)</div>
<div v-click class="text-2xl text-white mt-3">- Ajax (HTTP Request)</div>
<div v-click class="text-2xl text-white mt-3">- catchError</div>

<div v-click class="text-2xl text-white mt-10">Backend</div>
<div v-click class="text-2xl text-white mt-3">- Exception Handler</div>
<div v-click class="text-2xl text-white mt-3">- Try catch strategy</div>


<BarBottom  title="Taksu Demo Day #6">
  <Item text="Bayu Kurniawan">
    <carbon:user-avatar />
  </Item>
</BarBottom>

---

# Error Handling in RxJs

<div class="mt-20"></div>
<div class="text-2xl text-white my-3">Without error handling</div>

```ts
assignProfile(res: AssignProfile): Promise<AssignProfile> {
    return new Promise<AssignProfile>((resolve) => {
      this.api
        .assignRobotProfile(res)
        .subscribe((result) => resolve(result.Data));
    });
  }
```


<BarBottom  title="Taksu Demo Day #6">
  <Item text="Bayu Kurniawan">
    <carbon:user-avatar />
  </Item>
</BarBottom>

---

# Error Handling in RxJs

<div class="mt-20"></div>
<div class="text-2xl text-white my-3">With error handling</div>

```ts {all|4-6|7-9|8}
assignProfile(res: AssignProfile): Promise<AssignProfile> {
  return new Promise<AssignProfile>((resolve) => {
    this.api.assignRobotProfile(res).subscribe({
      next: (assignResp) => {
        resolve(assignResp.Data);
      },
      error: (e: HttpErrorResponse) => {
        this.uiService.openSnackbar('update', e.error.Error.Message);
      },
      complete: () => console.log('Observer got a complete notification'), 
    });
  });
}
```


<BarBottom  title="Taksu Demo Day #6">
  <Item text="Bayu Kurniawan">
    <carbon:user-avatar />
  </Item>
</BarBottom>