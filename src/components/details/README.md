# Details

## Introduction

Component for conditionally revealing content, using the details HTML element.

## Guidance

Find out when to use the Details component in your service in the [GOV.UK Design System](https://govuk-design-system-production.cloudapps.digital/components/details).

## Quick start examples

### Component default

[Preview the details component](http://govuk-frontend-review.herokuapp.com/components/details/preview)

#### Markup

    <details class="govuk-details">
      <summary class="govuk-details__summary">
        <span class="govuk-details__summary-text">
          Help with nationality
        </span>
      </summary>
      <div class="govuk-details__text">
        We need to know your nationality so we can work out which elections you’re entitled to vote in. If you can’t provide your nationality, you’ll have to send copies of identity documents through the post.
      </div>
    </details>

#### Macro

    {% from 'details/macro.njk' import govukDetails %}

    {{ govukDetails({
      "summaryText": "Help with nationality",
      "text": "We need to know your nationality so we can work out which elections you’re entitled to vote in. If you can’t provide your nationality, you’ll have to send copies of identity documents through the post."
    }) }}

### Details--expanded

[Preview the details--expanded example](http://govuk-frontend-review.herokuapp.com/components/details/expanded/preview)

#### Markup

    <details id="help-with-nationality" class="govuk-details" open>
      <summary class="govuk-details__summary">
        <span class="govuk-details__summary-text">
          Help with nationality
        </span>
      </summary>
      <div class="govuk-details__text">
        We need to know your nationality so we can work out which elections you’re entitled to vote in. If you can’t provide your nationality, you’ll have to send copies of identity documents through the post.
      </div>
    </details>

#### Macro

    {% from 'details/macro.njk' import govukDetails %}

    {{ govukDetails({
      "id": "help-with-nationality",
      "summaryText": "Help with nationality",
      "text": "We need to know your nationality so we can work out which elections you’re entitled to vote in. If you can’t provide your nationality, you’ll have to send copies of identity documents through the post.",
      "open": true
    }) }}

### Details--with-html

[Preview the details--with-html example](http://govuk-frontend-review.herokuapp.com/components/details/with-html/preview)

#### Markup

    <details class="govuk-details">
      <summary class="govuk-details__summary">
        <span class="govuk-details__summary-text">
          Where to find your National Insurance Number
        </span>
      </summary>
      <div class="govuk-details__text">
        Your National Insurance number can be found on
    <ul>
      <li>your National Insurance card</li>
      <li>your payslip</li>
      <li>P60</li>
      <li>benefits information</li>
      <li>tax return</li>
    </ul>

      </div>
    </details>

#### Macro

    {% from 'details/macro.njk' import govukDetails %}

    {{ govukDetails({
      "summaryText": "Where to find your National Insurance Number",
      "html": "Your National Insurance number can be found on\n<ul>\n  <li>your National Insurance card</li>\n  <li>your payslip</li>\n  <li>P60</li>\n  <li>benefits information</li>\n  <li>tax return</li>\n</ul>\n"
    }) }}

## Requirements

### Build tool configuration

When compiling the Sass files you'll need to define includePaths to reference the node_modules directory. Below is a sample configuration using gulp

    .pipe(sass({
      includePaths: 'node_modules/'
    }))

### Static asset path configuration

In order to include the images used in the components, you need to configure your app to show these assets. Below is a sample configuration using Express js:

    app.use('/assets', express.static(path.join(__dirname, '/node_modules/@govuk-frontend/frontend/assets')))

## Component arguments

If you are using Nunjucks,then macros take the following arguments

<table class="govuk-table">

<thead class="govuk-table__head">

<tr class="govuk-table__row">

<th class="govuk-table__header" scope="col">Name</th>

<th class="govuk-table__header" scope="col">Type</th>

<th class="govuk-table__header" scope="col">Required</th>

<th class="govuk-table__header" scope="col">Description</th>

</tr>

</thead>

<tbody class="govuk-table__body">

<tr class="govuk-table__row">

<th class="govuk-table__header" scope="row">summaryText</th>

<td class="govuk-table__cell ">string</td>

<td class="govuk-table__cell ">Yes</td>

<td class="govuk-table__cell ">Text to use within the summary element (the visible part of the details element)</td>

</tr>

<tr class="govuk-table__row">

<th class="govuk-table__header" scope="row">summaryHtml</th>

<td class="govuk-table__cell ">string</td>

<td class="govuk-table__cell ">Yes</td>

<td class="govuk-table__cell ">HTML to use within the summary element (the visible part of the details element). If this is provided, the summaryText argument will be ignored.</td>

</tr>

<tr class="govuk-table__row">

<th class="govuk-table__header" scope="row">text</th>

<td class="govuk-table__cell ">string</td>

<td class="govuk-table__cell ">Yes</td>

<td class="govuk-table__cell ">Text to use within the disclosed part of the details element.</td>

</tr>

<tr class="govuk-table__row">

<th class="govuk-table__header" scope="row">html</th>

<td class="govuk-table__cell ">string</td>

<td class="govuk-table__cell ">Yes</td>

<td class="govuk-table__cell ">HTML to use within the disclosed part of the details element. If this is provided, the text argument will be ignored.</td>

</tr>

<tr class="govuk-table__row">

<th class="govuk-table__header" scope="row">id</th>

<td class="govuk-table__cell ">string</td>

<td class="govuk-table__cell ">No</td>

<td class="govuk-table__cell ">Optional id</td>

</tr>

<tr class="govuk-table__row">

<th class="govuk-table__header" scope="row">classes</th>

<td class="govuk-table__cell ">string</td>

<td class="govuk-table__cell ">No</td>

<td class="govuk-table__cell ">Optional additional classes</td>

</tr>

<tr class="govuk-table__row">

<th class="govuk-table__header" scope="row">open</th>

<td class="govuk-table__cell ">boolean</td>

<td class="govuk-table__cell ">No</td>

<td class="govuk-table__cell ">If true, details will be expanded.</td>

</tr>

<tr class="govuk-table__row">

<th class="govuk-table__header" scope="row">attributes</th>

<td class="govuk-table__cell ">object</td>

<td class="govuk-table__cell ">No</td>

<td class="govuk-table__cell ">Any extra HTML attributes (for example data attributes) to add to the details element</td>

</tr>

</tbody>

</table>

### Setting up Nunjucks views and paths

Below is an example setup using express configure views:

    nunjucks.configure('node_modules/@govuk-frontend/frontend/components', {
      autoescape: true,
      cache: false,
      express: app
    })

## Contribution

Guidelines can be found at [on our Github repository.](https://github.com/alphagov/govuk-frontend/blob/master/CONTRIBUTING.md "link to contributing guidelines on our github repository")

## License

MIT