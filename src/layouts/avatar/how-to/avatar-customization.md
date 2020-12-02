# Avatar Customization

## Color customization

The avatar comes with default background color (grey). This can be easily customized to desired color by adding custom
class or directly selecting the avatar class from the CSS.

{% tab template="avatar/color", isDefaultActive=true %}

```html
<template>
    <div id='element'>
        <span class="e-avatar e-avatar-xlarge e-avatar-circle green">AJ</span>
        <span class="e-avatar e-avatar-xlarge e-avatar-circle violet">JK</span>
        <span class="e-avatar e-avatar-xlarge e-avatar-circle rose">EL</span>
        <span class="e-avatar e-avatar-xlarge e-avatar-circle blue">SR</span>
        <span class="e-avatar e-avatar-xlarge e-avatar-circle red">PD</span>
    </div>
</template>
<script>
import Vue from "vue";

export default {
  data() {
    return {};
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
    #element {
        display: flex;
        width: 400px;
        margin: 100px auto;
        border-radius: 3px;
        justify-content: center;
    }

    .e-avatar {
        margin: 2px;
    }

    .e-avatar.green {
        background-color: #87eb87;
    }

    .e-avatar.violet {
        background-color: #ee82ee;
    }

    .e-avatar.blue {
        background-color: #7171e4;
    }

    .e-avatar.red {
        background-color: #d86e6e;
    }

    .e-avatar.rose {
        background-color: #bc8f8f;
    }
</style>

```

{% endtab %}

## Customize avatar sizes

Even though the avatar comes with five predefined sizes, sometimes it's not enough. So, the avatar is designed in such a
way that the width and height will be relative to font-size. By changing the `font-size` of the avatar element, you
can change the width and height automatically.

{% tab template="avatar/custom-size", isDefaultActive=true %}

```html
<template>
    <div id='element'>
        <span class="e-avatar">26px</span>
        <span class="e-avatar">24px</span>
        <span class="e-avatar">22px</span>
        <span class="e-avatar">20px</span>
        <span class="e-avatar">18px</span>
    </div>
</template>
<script>
import Vue from "vue";

export default {
  data() {
    return {};
  }
}
</script>
<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
    #element {
        display: block;
        width: 400px;
        margin: 100px auto;
        border-radius: 3px;
    }

    #element :nth-child(5) {
        font-size: 18px;
    }

    #element :nth-child(4) {
        font-size: 20px;
    }

    #element :nth-child(3) {
        font-size: 22px;
    }

    #element :nth-child(2) {
        font-size: 24px;
    }

    #element :nth-child(1) {
        font-size: 26px;
    }
</style>

```

{% endtab %}

### Use various media in avatar

Avatars can be used with a wide variety of media formats like SVG, font-icons, images, letters, words, etc. Some of them are given below.

{% tab template="avatar/media-formats", isDefaultActive=true %}

```html
<template>
    <div id='element'>
        <div class="sample_container avatar-types">
            <div class="avatar-block">
                <!-- Card Component -->
                <div class="e-card e-avatar-showcase">
                    <div class="e-card-content">
                        <!-- XLarge Circle Avatar Component -->
                        <div class="e-avatar e-avatar-xlarge e-avatar-circle">
                          <img class="image" src="./pic01.png" alt="image"/>
                        </div>
                    </div>
                    <div class="e-card-content">
                        <div>Image</div>
                    </div>
                </div>
            </div>

            <div class="avatar-block">
                <!-- Card Component -->
                <div class="e-card e-avatar-showcase">
                    <div class="e-card-content">
                        <!-- XLarge Circle Avatar Component -->
                        <div class="e-avatar e-avatar-xlarge e-avatar-circle">
                            <div class="svg_icons chrome"></div>
                        </div>
                    </div>
                    <div class="e-card-content">
                        <div>SVG</div>
                    </div>
                </div>
            </div>

            <div class="avatar-block">
                <!-- Card Component -->
                <div class="e-card e-avatar-showcase">
                    <div class="e-card-content">
                        <!-- XLarge Circle Avatar Component -->
                        <div class="e-avatar e-avatar-xlarge e-avatar-circle">GR</div>
                    </div>
                    <div class="e-card-content">
                        <div>Initial</div>
                    </div>
                </div>
            </div>

            <div class="avatar-block">
                <!-- Card Component -->
                <div class="e-card e-avatar-showcase">
                    <div class="e-card-content">
                        <!-- XLarge Circle Avatar Component -->
                        <div class="e-avatar e-avatar-xlarge e-avatar-circle">
                            <div class="e-people icons"></div>
                        </div>
                    </div>
                    <div class="e-card-content">
                        <div>Font Icon</div>
                    </div>
                </div>
            </div>

            <div class="avatar-block">
                <!-- Card Component -->
                <div class="e-card e-avatar-showcase">
                    <div class="e-card-content">
                        <!-- XLarge Circle Avatar Component -->
                        <div class="e-avatar e-avatar-xlarge e-avatar-circle">User</div>
                    </div>
                    <div class="e-card-content">
                        <div>Word</div>
                    </div>
                </div>
            </div>

            <div class="avatar-block">
                <!-- Card Component -->
                <div class="e-card e-avatar-showcase">
                    <div class="e-card-content">
                        <!-- XLarge Circle Avatar Component -->
                        <div class="e-avatar e-avatar-xlarge e-avatar-circle custom">
                            <div class="e-people icons"></div>
                        </div>
                    </div>
                    <div class="e-card-content">
                        <div>Custom</div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import Vue from "vue";

export default {
  data() {
    return {};
  }
}
</script>
<style>
    @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-layouts/styles/material.css";
    #element {
        width: auto;
        margin: auto;
        border-radius: 3px;
        justify-content: center;
    }


    /* Media Quries for various devices */

    @media only screen and (max-width: 965px) {
        .sample_container.avatar-types {
            max-width: 265px;
            margin: auto;
            margin-top: 0;
        }
        .e-avatar-showcase.e-card {
            width: 120px;
        }
    }

    @media only screen and (min-width: 965px) {
        .sample_container.avatar-types {
            max-width: 488px;
            margin: auto;
            margin-top: 35px;
        }
        .e-avatar-showcase.e-card {
            width: 150px;
        }
    }

    .sample_container.avatar-types .avatar-block {
        display: inline-block;
        vertical-align: top;
    }

    /* Avatar image source in 'background-image' property */

     .e-avatar img.image {
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
    }

    /* SVG Icons */

    .chrome {
        background: transparent url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 32 32'%3E%3Cpath fill='%23ffffff' d='M16.033 11.049a5.155 5.155 0 1 1 0 10.312 5.156 5.156 0 0 1 0-10.312zM16.124 0c1.281-.003 9.659.318 14.268 9.043h-.016l.01.018c.33.578 3.745 6.94-.485 14.969 0 0-4.215 8.107-14.565 7.968l-.452-.012-.004.007-.004.007.02-.037c.564-.98 5.112-8.884 6.357-11.067l.016-.028.007-.008.04-.069.11-.127a7.085 7.085 0 0 0 1.457-2.967l.01-.046.035-.151c.088-.424.148-.944.128-1.549l-.006-.117v-.004l-.007-.143-.006-.07-.005-.079-.012-.116v-.01l-.001-.008-.016-.158a7.2 7.2 0 0 0-.096-.572l-.018-.081-.013-.064a9.801 9.801 0 0 0-.692-2.016c-.165-.243-.332-.489-.512-.733l-.142-.187 8.728-2.554s-10.538-.01-13.018-.001l.021.005H16.642l-.14-.013a7.034 7.034 0 0 0-1.132-.003l-.167.016h-.047l-.034-.001c-.193.002-1.213.045-2.492.764l-.005.003-.033.016a7.158 7.158 0 0 0-3.25 3.533l-.059.148-6.485-6.404s4.74 8.311 6.165 10.779l.065.113.023.088a7.14 7.14 0 0 0 7.777 5.118l.144-.02L14.854 32h-.027c-.667-.005-7.894-.234-12.744-7.906 0 0-4.925-7.698.37-16.573l.252-.411.001-.002C2.822 6.904 6.58.374 15.958.003c0 0 .057-.003.166-.003z'/%3E%3C/svg%3E") no-repeat 100% 100%;
    }

    .svg_icons {
        width: 32px;
        height: 32px;
        display: inline-block;
    }

    /* Card Customization */

    .e-avatar-showcase.e-card {
        height: 113px;
        padding: 5px;
        margin: 5px;
        box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
        border-radius: 8px;
    }

    .e-avatar-showcase.e-card .e-card-header .e-card-header-title {
        align-self: center;
        font-size: 18px;
        letter-spacing: 1px;
        text-shadow: #eaeaea 1px 1px 2px;
    }

    .e-avatar-showcase.e-card .e-card-header .e-card-sub-title {
        color: rgba(0, 0, 0, 0.75);
        white-space: pre-line;
        font-size: 14px;
        text-shadow: #eaeaea 1px 1px 2px;
    }

    .e-avatar-showcase.e-card .e-card-header .e-card-sub-title p {
        margin: 0;
    }

    .e-avatar-showcase.e-card .e-card-content {
        align-self: center;
        padding: 10px 0 10px 0;
        overflow: visible;
    }

    .e-avatar-showcase.e-card .e-card-content .e-avatar {
        font-size: 18px;
    }

    /* Font Icons */

    @font-face {
        font-family: 'Contacts';
        src: url(data:application/x-font-ttf;charset=utf-8;base64,AAEAAAAKAIAAAwAgT1MvMj0gSRgAAAEoAAAAVmNtYXDnEOdaAAABjAAAADhnbHlmiAnWagAAAcwAAADwaGVhZBD04psAAADQAAAANmhoZWEHiwNuAAAArAAAACRobXR4C9AAAAAAAYAAAAAMbG9jYQAwAHgAAAHEAAAACG1heHABDwA1AAABCAAAACBuYW1lby+ImAAAArwAAAIxcG9zdGUbI4AAAATwAAAAOwABAAADUv9qAFoEAAAAAAAD3QABAAAAAAAAAAAAAAAAAAAAAwABAAAAAQAAWW9ja18PPPUACwPoAAAAANb8zuYAAAAA1vzO5gAAAAAD3QPqAAAACAACAAAAAAAAAAEAAAADACkAAgAAAAAAAgAAAAoACgAAAP8AAAAAAAAAAQPwAZAABQAAAnoCvAAAAIwCegK8AAAB4AAxAQIAAAIABQMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAUGZFZABA5wDnAQNS/2oAWgPqAJYAAAABAAAAAAAABAAAAAPoAAAD6AAAAAAAAgAAAAMAAAAUAAMAAQAAABQABAAkAAAABAAEAAEAAOcB//8AAOcA//8AAAABAAQAAAABAAIAAAAAADAAeAACAAAAAAO+A+oADQAZAAA3FBYXIT4BNS4BJyEOARMeARc+ATcuAScOAS4YFwMzFxgDq4H+zYGr4QOCY2KCAwOCYmGCnCtOISFOK3qiAwOiAe1igwICg2JjggICggAAAAACAAAAAAPdA+oAFAAoAAABDgEHIicjDgEHLgEnLgEnPgE3HgEFFBYfARYfATcXFhc2JDcmJCcGBAOkBfK3KioXEFcpBBEMRUsBBfK3tvL8cVRLDggBBsQKLDDPARMFBf7tz87+7QI+ndEEBwI/Izh2DS+RVZ3RBATRnWCmN3BIETecAgcBBPK1tfIEBPIAAAAAABIA3gABAAAAAAAAAAEAAAABAAAAAAABAAgAAQABAAAAAAACAAcACQABAAAAAAADAAgAEAABAAAAAAAEAAgAGAABAAAAAAAFAAsAIAABAAAAAAAGAAgAKwABAAAAAAAKACwAMwABAAAAAAALABIAXwADAAEECQAAAAIAcQADAAEECQABABAAcwADAAEECQACAA4AgwADAAEECQADABAAkQADAAEECQAEABAAoQADAAEECQAFABYAsQADAAEECQAGABAAxwADAAEECQAKAFgA1wADAAEECQALACQBLyBDb250YWN0c1JlZ3VsYXJDb250YWN0c0NvbnRhY3RzVmVyc2lvbiAxLjBDb250YWN0c0ZvbnQgZ2VuZXJhdGVkIHVzaW5nIFN5bmNmdXNpb24gTWV0cm8gU3R1ZGlvd3d3LnN5bmNmdXNpb24uY29tACAAQwBvAG4AdABhAGMAdABzAFIAZQBnAHUAbABhAHIAQwBvAG4AdABhAGMAdABzAEMAbwBuAHQAYQBjAHQAcwBWAGUAcgBzAGkAbwBuACAAMQAuADAAQwBvAG4AdABhAGMAdABzAEYAbwBuAHQAIABnAGUAbgBlAHIAYQB0AGUAZAAgAHUAcwBpAG4AZwAgAFMAeQBuAGMAZgB1AHMAaQBvAG4AIABNAGUAdAByAG8AIABTAHQAdQBkAGkAbwB3AHcAdwAuAHMAeQBuAGMAZgB1AHMAaQBvAG4ALgBjAG8AbQAAAAACAAAAAAAAAAoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMBAgEDAQQABHVzZXIKY2hhdC0wMS13ZgAAAA==) format('truetype');
        font-weight: normal;
        font-style: normal;
    }

    .people,
    .e-people {
        font-family: 'Contacts';
    }

    .e-people:before {
        content: '\e700';
    }

    .e-avatar .e-people.icons {
        font-size: 24px;
    }

    /* Custom Avatar Background Color */

    .e-avatar.custom {
        background-color: blueviolet;
    }
</style>

```

{% endtab %}
