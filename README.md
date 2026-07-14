# MedSAM-with-text-prompts
Adapting medSAM to segment based on text prompts ( trained on the BCTV dataset)

This notebook explores how to adapt a segmentation model for highly specific medical tasks. The core objective is learning how to guide a vision model using natural language.

# Approach and Architecture
Extend the Segment Anything Model for Medical Images (MedSAM) by integrating text-based prompts to identify specific organs in CT scans.

Semantic Guidance: I utilized a pre-trained CLIP text encoder to convert organ names into fixed-dimensional vectors. These text embeddings replace the standard bounding box prompts and are passed directly into the multi-head cross-attention layers of the Mask Decoder.

Parameter Efficiency: To maintain computational efficiency, both the heavy Image Encoder and the CLIP Text Encoder are kept frozen. Only the Mask Decoder and a lightweight projection head are actively trained to map semantic meaning to visual boundaries.


# Visualizing the Output
The notebook includes visual segmentation plots to verify the alignment of our text prompts with the predicted masks. Below are examples of the model successfully locating target organs based purely on text input.

<figure>
  <img src="New Note.jpg">
  <figcaption> Orignal image with ground truth and the segmentation based on text prompt. </figcaption>
</figure>
