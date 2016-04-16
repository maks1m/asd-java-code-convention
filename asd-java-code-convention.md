## Java Code Conventions

Created by Oleksandr Tarasenko, last modified on Apr 08, 2016 Go to start of metadata

### Source files

#### File name
The source file name consists of the case-sensitive name of the top-level class it contains, plus the ".java" extension.

#### Encoding

Source files are encoded in UTF-8.

#### Code
Each Java source file contains a single public class or interface. When private classes and interfaces are associated with a public class, you can put them in the same source file as the public class. The public class should be the first class, enumeration or interface in the file.

#### Contents of source file
Java source files have the following ordering:
Description comments for all file if it contains more than one class or interface;
Non-static imports;
Static imports;
Class, interface or enumeration declaration.

#### Imports
Non-static imports should not have the star symbol ('\*') in the end. It means, that all classes should be imported explicitly.

#### Formating
**Block-like constructions**
- for;
- while;
- do-while;
- if-else;
- try-catch-finally.

Braces
In block-like constructions, open braces are in the same row with the keyword
Line break after the opening brace;
Line break before the closing brace;
Braces are used with if, else, for, do and while statements, even when the body is empty or contains only a single statement;
Line break after the closing brace if that brace terminates a statement or the body of a method, constructor or named class. For example, there is no line break after the brace if it is followed by else or a comma.

```java
return new MyClass() {
  @Override 
  public void doSomething() {
    if (exists()) {
      try {
        doSomethingElse();
      } catch (ProblemException e) {
        fixProblem();
      }
    }
  }
};
```

#### Tabs
use tabs instead of spaces to make indentations;
use 1 tab to make indentations for block-like constructs;
use 2 tabs to make indentations for wrapping rows.

#### Column limit
The column limit should be 160 symbols per line. Exceptions:
Lines, where obeying the column limit is not possible (for example, a long URL in Javadoc, or a long JSNI method reference).

#### Package and import statements.
** Whitespaces **

Beyond where required by the language or other style rules, and apart from literals, comments and Javadoc, a single ASCII space also appears in the following places only.
Separating any reserved word, such as if, for or catch, from an open parenthesis (() that follows it on that line
Separating any reserved word, such as else or catch, from a closing curly brace (}) that precedes it on that line
On both sides of any binary or ternary operator. This also applies to the following "operator-like" symbols:
the ampersand in a conjunctive type bound: <T extends Foo & Bar>
the pipe for a catch block that handles multiple exceptions: catch (FooException | BarException e)
the colon (:) in an enhanced for ("for each") statement
      4. On both sides of the double slash (//) that begins an end-of-line comment.
Enum classes
Each enum constant should be in separate line.
Naming
Rules common to all identifiers
Identifiers use only ASCII letters and digits and in two cases noted below underscores. Thus, each valid identifier name is matched by the regular expression "\w+". Using of Hungarian notation or using other not understandable prefixes is not allowed. Also, it is not allowed to use underscore as prefix or suffix. Using of not latin letters is prohibited.
Examples of not allowed names
product_;
_restriction;
iDays;
sName;
Rules by identifier type
Package names
Package names are all lowercase, with consecutive words simply concatenated together (no underscores). For example, "com.mybookingpal.channelpartner", not "com.mybookingpal.channelPartner" or "com.mybookingpal.channel_partner".
Class names
Class names are written in UpperCamelCase.
Class names are typically nouns or noun phrases. For example, Character or ImmutableList. Interface names may also be nouns or noun phrases (for example, List), but may sometimes be adjectives or adjective phrases instead (for example, Readable).
Method names
Method names are written in lowerCamelCase.
Method names are typically verbs or verb phrases. For example, sendMessage or stop.
Constant names
Constant names use CONSTANT_CASE: all uppercase letters, with words separated by underscores. But what is a constant, exactly?
Every constant is a static final field, but not all static final fields are constants. Before choosing constant case, consider whether the field really feels like a constant. For example, if any of that instance's observable state can change, it is almost certainly not a constant. Merely intending to never mutate the object is generally not enough. Examples:
// Constants
static final int NUMBER = 5;
static final ImmutableList<String> NAMES = ImmutableList.of("Ed", "Ann");
static final Joiner COMMA_JOINER = Joiner.on(',');  // because Joiner is immutable
static final SomeMutableType[] EMPTY_ARRAY = {};
enum SomeEnum { ENUM_CONSTANT }
 
// Not constants
static String nonFinal = "non-final";
final String nonStatic = "non-static";
static final Set<String> mutableCollection = new HashSet<String>();
static final ImmutableSet<SomeMutableType> mutableElements = ImmutableSet.of(mutable);
static final Logger logger = Logger.getLogger(MyClass.getName());
static final String[] nonEmptyArray = {"these", "can", "change"};
These names are typically nouns or noun phrases.
Non-constant field names
Non-constant field names (static or otherwise) are written in lowerCamelCase.
These names are typically nouns or noun phrases. For example, computedValues or index. 
Parameter names
Parameter names are written in lowerCamelCase.
One-character parameter names should be avoided.
Local variable names
Local variable names are written in lowerCamelCase, and can be abbreviated more liberally than other types of names.
However, one-character names should be avoided, except for temporary and looping variables.
Even when final and immutable, local variables are not considered to be constants, and should not be styled as constants.
Type variable names
Each type variable is named in one of two styles. A single capital letter, optionally followed by a single numeral (such as E, T, X, T2).
Constant names
Constant names use CONSTANT_CASE: all uppercase letters, with words separated by underscores. But what is a constant, exactly?
Every constant is a static final field, but not all static final fields are constants. Before choosing constant case, consider whether the field really feels like a constant. For example, if any of that instance's observable state can change, it is almost certainly not a constant. Merely intending to never mutate the object is generally not enough. Examples:
// Constants
static final int NUMBER = 5;
static final ImmutableList<String> NAMES = ImmutableList.of("Ed", "Ann");
static final Joiner COMMA_JOINER = Joiner.on(',');  // because Joiner is immutable
static final SomeMutableType[] EMPTY_ARRAY = {};
enum SomeEnum { ENUM_CONSTANT }
 
// Not constants
static String nonFinal = "non-final";
final String nonStatic = "non-static";
static final Set<String> mutableCollection = new HashSet<String>();
static final ImmutableSet<SomeMutableType> mutableElements = ImmutableSet.of(mutable);
static final Logger logger = Logger.getLogger(MyClass.getName());
static final String[] nonEmptyArray = {"these", "can", "change"};
These names are typically nouns or noun phrases.
Non-constant field names
Non-constant field names (static or otherwise) are written in lowerCamelCase.
These names are typically nouns or noun phrases. For example, computedValues or index. 
Parameter names
Parameter names are written in lowerCamelCase.
One-character parameter names should be avoided.
Local variable names
Local variable names are written in lowerCamelCase, and can be abbreviated more liberally than other types of names.
However, one-character names should be avoided, except for temporary and looping variables.
Even when final and immutable, local variables are not considered to be constants, and should not be styled as constants.
Type variable names
Each type variable is named in one of two styles. A single capital letter, optionally followed by a single numeral (such as E, T, X, T2).
Converting words or phrases to camel case
Sometimes there is more than one reasonable way to convert an English phrase into camel case, such as when acronyms or unusual constructs like "IPv6" or "iOS" are present. There is an algorithm how to convert words or phrases to camelCase:
 
Convert the phrase to plain ASCII and remove any apostrophes. For example, "Müller's algorithm" might become "Muellers algorithm".
Divide this result into words, splitting on spaces and any remaining punctuation (typically hyphens).
Recommended: if any word already has a conventional camel-case appearance in common usage, split this into its constituent parts (e.g., "AdWords" becomes "ad words"). Note that a word such as "iOS" is not really in camel case per se; it defies any convention, so this recommendation does not apply.
      3. Now lowercase everything (including acronyms), then uppercase only the first character of:
... each word, to yield upper camel case, or
... each word except the first, to yield lower camel case
      4. Finally, join all the words into a single identifier.
Note that the casing of the original words is almost entirely disregarded. Examples:
Prose form
Correct
Incorrect
"XML HTTP request"	XmlHttpRequest	 XMLHTTPRequest
"new customer ID"	newCustomerId	newCustomerID
"inner stopwatch"	innerStopwatch	innerStopWatch
"supports IPv6 on iOS?"	 supportsIpv6OnIos	 supportsIPv6OnIOS
"YouTube importer"	 YouTubeImporter	 
JavaDoc
Basics
The basic formatting of JavaDoc commentaries looks like this:
/**
 * Some JavaDoc commentaries
 *
 */
The JavaDoc commentaries for methods and classes should be explicit before the annotations for  the entity, those commentaries are for.
@-clauses
Any of the standard "at-clauses" that are used appears in the order @param, @return, @throws, @deprecated, and these four types never appear with an empty description. When an at-clause doesn't fit on a single line, continuation lines are indented four (or more) spaces from the position of the @. Bad example:
/**
 * invoke an event so that channel listeners can take care of
 * updating the respective channels
 * now check if the product id belongs to ChannelProductMap
 *
 * @param sqlSession
 * @param listTobeActivatedProducts
 */
private void invokeEventToActivateProductsOnChannels(SqlSession sqlSession, List<String> listTobeActivatedProducts) {
Classes
Each class should have a description using JavaDoc commentaries. Good example:
/**
 * The {@code Integer} class wraps a value of the primitive type
 * {@code int} in an object. An object of type {@code Integer}
 * contains a single field whose type is {@code int}.
 *
 * <p>In addition, this class provides several methods for converting
 * an {@code int} to a {@code String} and a {@code String} to an
 * {@code int}, as well as other constants and methods useful when
 * dealing with an {@code int}.
 *
 * <p>Implementation note: The implementations of the "bit twiddling"
 * methods (such as {@link #highestOneBit(int) highestOneBit} and
 * {@link #numberOfTrailingZeros(int) numberOfTrailingZeros}) are
 * based on material from Henry S. Warren, Jr.'s <i>Hacker's
 * Delight</i>, (Addison Wesley, 2002).
 *
 * @author  Lee Boynton
 * @author  Arthur van Hoff
 * @author  Josh Bloch
 * @author  Joseph D. Darcy
 * @since JDK1.0
 */
public final class Integer extends Number implements Comparable<Integer> {
 Bad example of using JavaDoc commentaries, when they are generated by IDE: 
/**
 * Created by Petr Sidorov on 29.03.16.
 */
public class SomeClass {
}
Methods
Each public method of a class also should have a description using JavaDoc commentaries. Good example:
 
 Expand source
Exception: self-explanatory methods
Javadoc is optional for "simple, obvious" methods like getFoo, in cases where there really and truly is nothing else worthwhile to say but "Returns the foo".
It is not appropriate to cite this exception to justify omitting relevant information that a typical reader might need to know. For example, for a method named getCanonicalName, don't omit its documentation (with the rationale that it would say only /** Returns the canonical name. */) if a typical reader may have no idea what the term "canonical name" means.
