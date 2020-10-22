This repository is for review and discussion of the UTF-8 classes
for the Unicon programming language.

In relation to mapping lower to upper case or upper to lower case, there are a
number of difficulties that will be encountered. These are documented on the
Unicode.org website. To that end, three files have been copied from that site
and placed here for reference in developing appropriate mapping regimes. These
mapping sets will need to be on a langauge by language basis and there are
situations where there is no 1-1 mapping available for lower to upper ot upper
to lower case.

There is now the corrseponding methods and operator overload facilities for
dealing with the use of UTF8 strings as numeric values and allowing these values
to be converted to the appropriate numeric values for use in nemeric operations.

There are now consistent runtime errors in essentially all places where Unicon has
runtime errors occurring for Unicon strings. The error messages are of the same
standard format as the underlying Unicon system and uses the same standard error
codes as found in the Unicon runtime.

The following is a list of the applicable packages and the associated classes
with each method. Inculded in this list for each pckage are the defined procedures.

package ErrorSystem
class ErrorSystem
    method __proc_components(level, pos)
    method AbortIfDebug(param[])
    method AbortMessage(errorcode, file, lineno, param[])
    method Caller(addedlvl)
    method CallingComponents(name)
    method ClassCalling(level)
    method Debug(mode)
    method DebugMode()
    method ErrorOut(errorfile, writeappend)
    method IsOn()
    method MethodCalling(level)
    method NotInDebugMode()
    method Off()
    method On()
    method PackageCalling(level)
    method ParamCalling(level)
    method PrintMessage(param[])
    method ProcedureCalling(level)
    method StopMessage(param[])

procedure AllOff()
procedure AllOn()
procedure trace(message[])


package ClassObject
class ClassClass : ClassObject
    method __InitClass()
    method SetClass(obj)

    method Addition(val1, val2)
    method Divide(val1, val2)
    method Minus(val1, val2)
    method Modulus(val1, val2)
    method Multiply(val1, val2)
    method Negate(val)
    method UnaryPlus(val)
    method Power(val1, val2)

    method Equals(val1, val2)
    method GTorEqual(val1, val2)
    method Greater(val1, val2)
    method LTorEqual(val1, val2)
    method Less(val1, val2)
    method Nequal(val1, val2)

    method Integer(val)
    method Numeric(val)
    method Real(val)

class ClassObject : ErrorSystem
    abstract method String()
    method __call_by_method_name(methname, params[])
    method ClassName()
    method Clone()
    method Copy()
    method operator_overload_error_error(methname)
    method Serial()
    method set_operator_overload_abort(noabort)

    method Addition(val)
    method Divide(val)
    method Minus(val)
    method Modulus(val)
    method Multiply(val)
    method Negate()
    method UnaryPlus()
    method Power(val)

    method Equals(val)
    method GTorEqual(val)
    method Greater(val)
    method LTorEqual(val)
    method Less(val)
    method Nequal(val)

    method Integer()
    method Numeric()
    method Real()

    method __add__(y)
    method __div__(y)
    method __minus__(y)
    method __mod__(y)
    method __mult__(y)
    method __neg__()
    method __number__()
    method __powr__(y)

    method __eqv__(y)
    method __neqv__(y)

    method __lexeq__(y)
    method __lexge__(y)
    method __lexgt__(y)
    method __lexle__(y)
    method __lexlt__(y)
    method __lexne__(y)

    method __numeq__(y)
    method __numge__(y)
    method __numgt__(y)
    method __numle__(y)
    method __numlt__(y)
    method __numne__(y)

    method __cat__(y)
    method __lcat__(y)

    method __compl__()
    method __diff__(y)
    method __inter__(y)
    method __union__(y)

    method __bang__()
    method __random__()
    method __refresh__()
    method __sect__(y, z)
    method __size__()
    method __subsc__(y)
    method __tabmat__()
    method __toby__(y, z)

procedure __NewNotSet(val)
procedure AlreadyRun(object_tested)
procedure DeepCopy(A, cache)
procedure Execute(object_or_class_value)
procedure IsObjectOf(value, expectedtypes[])
procedure IsObject(value_tested)
procedure ObjectProperties(object_or_classname)
procedure set_operator_overload_error_messages()
procedure SuperClass(this_object)
procedure HasMethod(val, methodname)


package UTF8
class UTF8 : ClassClass
    method __Initialise()
    method __ActualPos(ustr, i)
    method __Coerce(val)
    method __GetAt(ustr, i, j)

    method BOMFound(str)
    method SkipBOM(str)
    method Valid(str)
    method ByteTranslate(byte)
    method Multibyte(codepoint)
    method SpecialString(str)
    method ToUnicode32(ustr)
    method Unicode32To(unicode)
    method HexTo(hexcode)
    method DecimalTo(num)

    method AmpPos()

    method Equiv(val1, val2)
    method Nequiv(val1, val2)

    method LexEquals(str1, str2)
    method LexGTorEq(str1, str2)
    method LexGT(str1, str2)
    method LexLTorEq(str1, str2)
    method LexLT(str1, str2)
    method LexNE(str1, str2)

    method Concatenate(ustr1, ustr2)

    method Complement(val)
    method Difference(val1, val2)
    method Intersect(val1, val2)
    method Union(val1, val2)

    method ForEach(str)
    method Size(str)
    method Random(str)
    method Subsection(ustr, i, j)
    method Subscript(str, i)
    method TabMatch(str)

    method Any(uset, ustr, i, j)
    method Bal(uset, usetopen, usetclose, ustr, i, j)
    method Center(ustr, i, pstr)
    method Char(i)
    method Cset(val)
    method Detab(ustr, i[])
    method Entab(ustr, i[])
    method Find(ustr1, ustr, i, j)
    method Left(ustr, i, pstr)
    method Many(uset, ustr, i, j)
    method Map(ustr, ustr1, ustr2)
    method Match(ustr1, ustr, i, j)
    method Move(i)
    method Ord(ustr)
    method Pos(i)
    method Repl(ustr, i)
    method Reverse(ustr)
    method Right(ustr, i, pstr)
    method String(val)
    method Tab(i)
    method Trim(ustr, uset, i, allutf8blanks)
    method Upto(uset, ustr, i, j)

class __UTF8Object : ClassObject
    method Data()

    method Complement()
    method Difference(val)
    method Intersect(val)
    method Union(val)

    method Equiv(val)
    method Nequiv(val)

    method LexEquals(str)
    method LexGTorEq(str)
    method LexGT(str)
    method LexLTorEq(str)
    method LexLT(str)
    method LexNE(str)

    method ForEach()
    method Random()
    method TabMatch()
    method Size()
    method Concatenate(ustr)
    method Subsection(i, j)
    method Subscript(i)
    method String()
    method Invalid()

class UTF8Set : ClassClass
    method __Coerce(val)

    method Complement(uset)
    method Difference(uset1, uset2)
    method Intersect(uset1, uset2)
    method Union(uset1, uset2)

    method ForEach(val)
    method Size(val)
    method String(val)
    method Subscript(val, i)
    method Member(uset, val[])

    method Space()
    method UTF8Spaces()
    method Ascii()
    method Rparens()
    method Lparens()
    method All()
    method MaxSize()
    method Defined(str)

class __UTF8SetObject : ClassObject
    method __DebugPrint(modifier, val, uset)

    method Equiv(uset)
    method Nequiv(uset)

    method LexEquals(str)
    method LexGTorEq(str)
    method LexGT(str)
    method LexLTorEq(str)
    method LexLT(str)
    method LexNE(str)

    method Complement()
    method Difference(val)
    method Intersect(val)
    method Union(val)

    method ForEach()
    method Size()
    method Subscript(i)
    method Member(c[])

    method UTF8Value()
    method String()



Bruce Rennie
