Exploits the internet scale data diffusion models like DALLE are trained on - DALLE has greater semantic understanding, and in this paper is used as a kind of imagination engine for robotic rearrangement tasks.

**Algorithm**
First a picture is taken of a table top scene, and then three different models are used on each object in the scene. One generates a mask, one an embedding, and one a caption. A separate NLP model is used to pick out the noun in the generated caption, which is appended into a minimalistic prompt for DALLE. DALLE is conditioned on the image masks, and generates a rearrangement of the object which should be more pleasing to humans (since most training data for DALLE should have already pleasing arrangements <- relatively weak assumption?). The images sampled from DALLE are checked for correct number of objects + algorithms are used to calculate a similarity score between the original image and then generated one. The most similar arrangement is used (<- again, seems like a weak assumption to make. The best generation might be relatively far from the current state). The objects in the generation are masked out, resized, and their mask is used to find a translation between the original mask and new one, and then IK is used to move the objects.

**Thoughts**
- relatively limited in real-world deployment. Only works on directly pointed down at table top.
- useful only for relatively limited environments like table setting
- a lot of engineering went into getting good results from the inconsistent/occasionally poor/unrealistic generations