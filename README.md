## Installation

Set .env variables:

```properties
PORT=
AWS_KEY=
AWS_SECRET=
AWS_REGION=
AWS_BUCKET=
```

Install dependencies:

```shell
npm install
```

Execute the code:

```shell
npm start
```

## API

An API request may provide the `Config` properties either as URL parameters in a `GET` request, or as a JSON object in a `POST` request.
```typescript
export enum InputType {
  S3 = 's3',
  URL = 'url',
  LOCAL = 'local'
}

export enum OutputType {
  S3 = 's3',
  LOCAL = 'local'
}

export type Config = {
  inputPath: string;
  outputPath: string;
  inputType: InputType;
  outputType: OutputType;
};
```
`inputPath` and `outputPath` have different formats depending on the `inputType` and `outputType`. Using the `s3` type requires setting the object key. Using the `local` type requires providing the path to a local file which will be found relative to the `input` or `output` folders in the root of the repository. Using the `url` type requires `inputPath` to be a URL.