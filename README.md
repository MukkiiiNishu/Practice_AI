RequestBody body = RequestBody.create(jsonBody, MediaType.get("application/json; charset=utf-8"));

        // Build the request with Authorization header
        Request request = new Request.Builder()
                .url(url)
                .post(body)
                .addHeader("Authorization", "Bearer " + token) // Add Authorization header
                .addHeader("Content-Type", "application/json") // Optional: Explicitly set content type
                .build();

        try {
            // Execute the POST request
            try (Response response = httpClient.newCall(request).execute()) {
                if (response.isSuccessful()) {
                    System.out.println("Response: " + response.body().string());
                } else {
                    System.out.println("Request failed with status code: " + response.code());
                }
            }
        } catch (IOException e) {
            System.out.println("Request failed: " + e.getMessage());
        }
