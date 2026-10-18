# M-Shots Prompting — Experiment Report

## Objective
Compare zero-shot, one-shot and few-shot extraction of product name, price and category.

## Method
Five fixed product descriptions were tested with each strategy using the same model and output instructions. One-shot uses one demonstration; few-shot uses three. Expected outputs were defined in advance.

## Results
- zero-shot: field accuracy 0.0%; valid JSON/schema 0.0%; exact matches 0.0%; hallucinated missing values 0; API errors 0.
- one-shot: field accuracy 93.3%; valid JSON/schema 100.0%; exact matches 80.0%; hallucinated missing values 0; API errors 0.
- few-shot: field accuracy 93.3%; valid JSON/schema 100.0%; exact matches 80.0%; hallucinated missing values 0; API errors 0.

## Errors and hallucinations
- zero-shot, case 1: output='```json\n{\n  "product_name": "SoundWave Pro wireless headphones",\n  "price": "€89.99",\n  "category": "Electronics"\n}\n```'; expected={'product_name': 'SoundWave Pro', 'price': '€89.99', 'category': 'Electronics'}; error=None
- zero-shot, case 2: output='```json\n{\n  "product_name": "UrbanTrail Backpack",\n  "price": "€49.50",\n  "category": "Accessories"\n}\n```'; expected={'product_name': 'UrbanTrail Backpack', 'price': '€49.50', 'category': 'Accessories'}; error=None
- zero-shot, case 3: output='```json\n{\n  "product_name": "FreshBrew Coffee Maker",\n  "price": "€79.00",\n  "category": "Home Appliances"\n}\n```'; expected={'product_name': 'FreshBrew Coffee Maker', 'price': '€79.00', 'category': 'Home Appliances'}; error=None
- zero-shot, case 4: output='```json\n{\n  "product_name": "The FlexFit Yoga Mat",\n  "price": "€24.99",\n  "category": "Sports"\n}\n```'; expected={'product_name': 'FlexFit Yoga Mat', 'price': '€24.99', 'category': 'Sports'}; error=None
- zero-shot, case 5: output='```json\n{\n  "product_name": "LunaGlow Desk Lamp",\n  "price": null,\n  "category": "Lighting"\n}\n```'; expected={'product_name': 'LunaGlow Desk Lamp', 'price': None, 'category': 'Lighting'}; error=None
- one-shot, case 1: output='{"product_name":"SoundWave Pro wireless headphones","price":"€89.99","category":"Electronics"}'; expected={'product_name': 'SoundWave Pro', 'price': '€89.99', 'category': 'Electronics'}; error=None
- few-shot, case 1: output='{"product_name":"SoundWave Pro wireless headphones","price":"€89.99","category":"Electronics"}'; expected={'product_name': 'SoundWave Pro', 'price': '€89.99', 'category': 'Electronics'}; error=None

## Conclusion
Examples can clarify the intended extraction pattern, but do not guarantee improved accuracy. Because the schema is already explicit in all three prompts, differences may be small. The missing-price example tests whether the model invents unavailable data. Repeat the experiment with more descriptions and multiple runs before drawing broad conclusions.