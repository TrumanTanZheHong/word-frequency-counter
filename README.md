# word-frequency-counter
reads a txt file and outputs the top 10 words with the highest frequency 
import string

    def main():
        file_path = input("Enter the name of the txt file: ")  # Name of the file in the same directory
    
        try:
            with open(file_path, 'r', encoding='utf-8') as f:
                content = f.read()
                wordcount = word_frequencies(content)
                print("Word frequencies for top 10 words:")
                print_top_words(wordcount)
        except FileNotFoundError:
            print(f"Error: The file '{file_path}' was not found.")
        except Exception as e:
            print(f"An error occurred: {e}")
    
    def word_frequencies(content):
        wordcount = {}
        for word in content.split():
            word = word.lower().translate(str.maketrans('', '', string.punctuation))  # Remove punctuation
            if word in wordcount:
                wordcount[word] += 1
            else:
                wordcount[word] = 1
        return wordcount
    
    def print_top_words(wordcount, n=10):
        sorted_words = sorted(wordcount.items(), key=lambda x: x[1], reverse=True)
        for word, count in sorted_words[:n]:
            print(f"{word}: {count}")
    
    if __name__ == "__main__":
        main()
