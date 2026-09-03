# mourn-badge-css
A CSS boilerplate class for a mourn with a hover message and a donation link.

<img width="418" height="195" alt="demo" src="https://github.com/user-attachments/assets/4fa848fc-0354-463b-8fa8-faee46181042" />

## Hugo Setup
If you use [goHugo](https://gohugo.io/) for your website, you can do the following.
1. Copy the `mourn-badge.css` into your theme `css` file.
2. If you don't have a [`data` folder](https://gohugo.io/content-management/data-sources/) then, create a `data` folder inside the root directory of your site.
3. Create a file named `mourn.yml` in this directory. Use the following example:
```yml
mode: true
message: In mourning for the victims of the flash floods in Nepal, I extend my deepest condolences to the affected families and communities. I encourage you to consider donating to the "Prime Minister's Disaster Relief Fund" of Nepal at donate.gov.np/. Your contribution will help those in need during this difficult time.
url: https://donate.gov.np/
```
4. To keep the mourn badge next to your site logo, simply add the below code to your site logo’s HTML, and customise as needed. This will be located inside the `partials/header.html` file in HUGO.
```html
{{ if site.Data.mourn.mode }}
  <a href="{{ site.Data.mourn.url }}" target="_blank" rel="noopener noreferrer">
    <span class="mourn-badge" aria-label="mourning" data-tooltip="{{ site.Data.mourn.message }}"></span>
  </a>
{{ end }}
```

### Additional setup for [Decap CMS](https://decapcms.org/)
Below the `collections` variable in the `static/admin/config.yml`, add the following line:
```yml
  - name: "settings"
    label: "Site Settings"
    editor:
      preview: false
    files:
      - label: "Mourn Settings"
        name: "mourn"
        file: "data/mourn.yml"
        fields:
          - label: "Enable Mourn Mode"
            name: "mode"
            widget: "boolean"
            default: false
            hint: "Toggle to show or hide the mourn status next to the MUNSS logo at the navigation bar."
          - label: "Mourn Message"
            name: "message"
            widget: "string"
            required: false
            hint: "The text to display when mourn mode is active. When hover over the mourn symbol, this text will be shown."
          - label: "URL"
            name: "url"
            widget: "string"
            required: false
            hint: "The URL to link to when the mourn symbol is clicked."
```

© 2026 Damodar Rajbhandari
