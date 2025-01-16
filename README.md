# Recommendation-system
**company**:CODTECH IT SOLUTION PVT.LTD
**NAME**:H.Abirami
**INTERN ID**:CT08GNX
**DOMAIN**:JAVA programming
**BATCH DURATION**:25-12-24 to 25-01-25
**MENTOR NAME**:NEELA SANTHOSH
# ENTER THE DESCRIPTION  OF TASK PERFORMED WITHIN 500 WORDS
A recommendation system is a type of information filtering system that seeks to predict the rating or preference a user would give to an item. These systems are widely used in various applications, such as e-commerce, streaming services, and social media platforms.

Types of Recommendation Systems
Collaborative Filtering: This method makes automatic predictions about the interests of a user by collecting preferences from many users. It can be user-based or item-based.

Content-Based Filtering: This method recommends items based on the features of the items and a profile of the user's preferences.

Hybrid Methods: These combine collaborative and content-based filtering to improve recommendation accuracy.

Building a Collaborative Filtering Recommendation System in Java
Let's focus on building a collaborative filtering recommendation system using Java. We'll use the Apache Commons Math library for mathematical operations.

Set Up Your Environment:

Ensure you have the Java Development Kit (JDK) installed.
# PROGRAM
import org.apache.mahout.cf.taste.impl.model.file.FileDataModel;
import org.apache.mahout.cf.taste.impl.neighborhood.NearestNUserNeighborhood;
import org.apache.mahout.cf.taste.impl.recommender.GenericUserBasedRecommender;
import org.apache.mahout.cf.taste.impl.similarity.PearsonCorrelationSimilarity;
import org.apache.mahout.cf.taste.model.DataModel;
import org.apache.mahout.cf.taste.neighborhood.UserNeighborhood;
import org.apache.mahout.cf.taste.recommender.RecommendedItem;
import org.apache.mahout.cf.taste.similarity.UserSimilarity;

import java.io.File;
import java.util.List;

public class NewClass{
    public static void main(String[] args) {
        try {
            // Load data from a file
            DataModel model = new FileDataModel(new File("C:\\Users\\Abirami H\\Downloads\\data.csv"));

            // Compute user similarity using Pearson correlation
            UserSimilarity similarity = new PearsonCorrelationSimilarity(model);

            // Find a neighborhood of N nearest users
            UserNeighborhood neighborhood = new NearestNUserNeighborhood(2, similarity, model);

            // Create the recommender
            GenericUserBasedRecommender recommender = new GenericUserBasedRecommender(model, neighborhood, similarity);

            // Recommend items for a specific user
            int userId = 1; // Example user
            List<RecommendedItem> recommendations = recommender.recommend(userId, 3);

            // Print recommendations
            for (RecommendedItem recommendation : recommendations) {
                System.out.println("Recommended Item ID: " + recommendation.getItemID() +
                                   " | Preference Score: " + recommendation.getValue());
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}  
# OUTPUT
![Image](https://github.com/user-attachments/assets/d7bfa58b-1d9a-48d4-a690-d08df159558e)

