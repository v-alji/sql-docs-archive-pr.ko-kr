---
title: UDT 데이터 조작 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- CAST function
- data deletions [CLR integration]
- data insertions [CLR integration]
- CONVERT function
- data updates [CLR integration]
- comparing data
- updating data [CLR integration]
- removing data
- IsByteOrdered property
- variables [CLR integration]
- data manipulation [CLR integration]
- user-defined types [CLR integration], data manipulation
- deleting data
- UDTs [CLR integration], data manipulation
- invoking UDT methods
- inserting data
ms.assetid: 51b1a5f2-7591-4e11-bfe2-d88e0836403f
author: rothja
ms.author: jroth
ms.openlocfilehash: 75810a2ffd92130e45025f742d43ba7917d73992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730747"
---
# <a name="manipulating-udt-data"></a><span data-ttu-id="a887f-102">UDT 데이터 조작</span><span class="sxs-lookup"><span data-stu-id="a887f-102">Manipulating UDT Data</span></span>
  [!INCLUDE[tsql](../../includes/tsql-md.md)]<span data-ttu-id="a887f-103">에서는 UDT(사용자 정의 형식) 열의 데이터를 수정할 때 INSERT, UPDATE 또는 DELETE 문에 대한 특별한 구문을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-103">provides no specialized syntax for INSERT, UPDATE, or DELETE statements when modifying data in user-defined type (UDT) columns.</span></span> <span data-ttu-id="a887f-104">[!INCLUDE[tsql](../../includes/tsql-md.md)] CAST 또는 CONVERT 함수는 네이티브 데이터 형식을 UDT 형식으로 캐스트하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-104">The [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST or CONVERT functions are used to cast native data types to the UDT type.</span></span>  
  
## <a name="inserting-data-in-a-udt-column"></a><span data-ttu-id="a887f-105">UDT 열에 데이터 삽입</span><span class="sxs-lookup"><span data-stu-id="a887f-105">Inserting Data in a UDT Column</span></span>  
 <span data-ttu-id="a887f-106">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 세 개의 샘플 데이터 행을 **Points** 테이블에 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-106">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements insert three rows of sample data into the **Points** table.</span></span> <span data-ttu-id="a887f-107">**Point** 데이터 형식은 UDT의 속성으로 노출 되는 X 및 Y 정수 값으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-107">The **Point** data type consists of X and Y integer values that are exposed as properties of the UDT.</span></span> <span data-ttu-id="a887f-108">CAST 또는 CONVERT 함수를 사용 하 여 쉼표로 구분 된 X 및 Y 값을 **Point** 형식으로 캐스팅 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-108">You must use either the CAST or CONVERT function to cast the comma-delimited X and Y values to the **Point** type.</span></span> <span data-ttu-id="a887f-109">처음 두 문은 CONVERT 함수를 사용 하 여 문자열 값을 **Point** 형식으로 변환 하 고, 세 번째 문은 CAST 함수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-109">The first two statements use the CONVERT function to convert a string value to the **Point** type, and the third statement uses the CAST function:</span></span>  
  
```  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '3,4'));  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '1,5'));  
INSERT INTO dbo.Points (PointValue) VALUES (CAST ('1,99' AS Point));  
```  
  
## <a name="selecting-data"></a><span data-ttu-id="a887f-110">데이터 선택</span><span class="sxs-lookup"><span data-stu-id="a887f-110">Selecting Data</span></span>  
 <span data-ttu-id="a887f-111">다음 SELECT 문은 UDT의 이진 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-111">The following SELECT statement selects the binary value of the UDT.</span></span>  
  
```  
SELECT ID, PointValue FROM dbo.Points  
```  
  
 <span data-ttu-id="a887f-112">읽을 수 있는 형식으로 표시 된 출력을 보려면 값을 `ToString` 해당 문자열 표현으로 변환 하는 **Point** UDT의 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-112">To see the output displayed in a readable format, call the `ToString` method of the **Point** UDT, which converts the value to its string representation.</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="a887f-113">다음 결과가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-113">This produces the following results.</span></span>  
  
```  
IDPointValue  
----------  
13,4  
21,5  
31,99  
```  
  
 <span data-ttu-id="a887f-114">[!INCLUDE[tsql](../../includes/tsql-md.md)] CAST 및 CONVERT 함수를 사용하여 동일한 결과를 얻을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-114">You can also use the [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST and CONVERT functions to achieve the same results.</span></span>  
  
```  
SELECT ID, CAST(PointValue AS varchar)   
FROM dbo.Points;  
  
SELECT ID, CONVERT(varchar, PointValue)   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="a887f-115">**Point** UDT는 X 및 Y 좌표를 속성으로 노출 하 여 개별적으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-115">The **Point** UDT exposes its X and Y coordinates as properties, which you can then select individually.</span></span> <span data-ttu-id="a887f-116">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 X 및 Y 좌표를 개별적으로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-116">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement selects the X and Y coordinates separately:</span></span>  
  
```  
SELECT ID, PointValue.X AS xVal, PointValue.Y AS yVal   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="a887f-117">X 및 Y 속성은 결과 집합에 표시되는 정수 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-117">The X and Y properties return an integer value, which is displayed in the result set.</span></span>  
  
```  
IDxValyVal  
----------  
134  
215  
3199  
```  
  
## <a name="working-with-variables"></a><span data-ttu-id="a887f-118">변수 작업</span><span class="sxs-lookup"><span data-stu-id="a887f-118">Working with Variables</span></span>  
 <span data-ttu-id="a887f-119">DECLARE 문에 변수를 사용하여 UDT 형식에 변수를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-119">You can work with variables using the DECLARE statement to assign a variable to a UDT type.</span></span> <span data-ttu-id="a887f-120">다음 문은 [!INCLUDE[tsql](../../includes/tsql-md.md)] SET 문을 사용하여 값을 할당하고 변수에서 UDT의 `ToString` 메서드를 호출하여 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-120">The following statements assign a value using the [!INCLUDE[tsql](../../includes/tsql-md.md)] SET statement and display the results by calling the UDT's `ToString` method on the variable:</span></span>  
  
```  
DECLARE @PointValue Point;  
SET @PointValue = (SELECT PointValue FROM dbo.Points  
    WHERE ID = 2);  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 <span data-ttu-id="a887f-121">결과 집합에 변수 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-121">The result set displays the variable value:</span></span>  
  
```  
PointValue  
----------  
-1,5  
```  
  
 <span data-ttu-id="a887f-122">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 변수 할당에 SET 대신 SELECT를 사용하여 동일한 결과를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-122">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements achieve the same result using SELECT rather than SET for the variable assignment:</span></span>  
  
```  
DECLARE @PointValue Point;  
SELECT @PointValue = PointValue FROM dbo.Points  
    WHERE ID = 2;  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 <span data-ttu-id="a887f-123">변수 할당에 SELECT 및 SET를 사용할 경우의 차이점은 SELECT를 사용하면 하나의 SELECT 문에서 여러 변수를 할당할 수 있는 반면 SET 구문에서는 각 변수 할당에 고유한 SET 문이 필요하다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-123">The difference between using SELECT and SET for variable assignment is that SELECT allows you to assign multiple variables in one SELECT statement, whereas the SET syntax requires each variable assignment to have its own SET statement.</span></span>  
  
## <a name="comparing-data"></a><span data-ttu-id="a887f-124">데이터 비교</span><span class="sxs-lookup"><span data-stu-id="a887f-124">Comparing Data</span></span>  
 <span data-ttu-id="a887f-125">클래스를 정의할 때 `IsByteOrdered` 속성을 `true`로 설정한 경우 비교 연산자를 사용하여 UDT의 값을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-125">You can use comparison operators to compare values in your UDT if you have set the `IsByteOrdered` property to `true` when defining the class.</span></span> <span data-ttu-id="a887f-126">자세한 내용은 [사용자 정의 형식 만들기](creating-user-defined-types.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a887f-126">For more information, see [Creating a User-Defined Type](creating-user-defined-types.md).</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS Points   
FROM dbo.Points  
WHERE PointValue > CONVERT(Point, '2,2');  
```  
  
 <span data-ttu-id="a887f-127">값 자체가 비교 가능한 경우 `IsByteOrdered` 설정에 관계없이 UDT의 내부 값을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-127">You can compare internal values of the UDT regardless of the `IsByteOrdered` setting if the values themselves are comparable.</span></span> <span data-ttu-id="a887f-128">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 X가 Y보다 큰 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-128">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement selects rows where X is greater than Y:</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points  
WHERE PointValue.X < PointValue.Y;  
```  
  
 <span data-ttu-id="a887f-129">일치하는 PointValue를 검색하는 이 쿼리와 같이 변수에 비교 연산자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-129">You can also use comparison operators with variables, as shown in this query that searches for a matching PointValue.</span></span>  
  
```  
DECLARE @ComparePoint Point;  
SET @ComparePoint = CONVERT(Point, '3,4');  
SELECT ID, PointValue.ToString() AS MatchingPoint   
FROM dbo.Points  
WHERE PointValue = @ComparePoint;  
```  
  
## <a name="invoking-udt-methods"></a><span data-ttu-id="a887f-130">UDT 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="a887f-130">Invoking UDT Methods</span></span>  
 <span data-ttu-id="a887f-131">[!INCLUDE[tsql](../../includes/tsql-md.md)]에서 UDT에 정의된 메서드를 호출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-131">You can also invoke methods that are defined in your UDT in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a887f-132">**Point** 클래스에는, 및 라는 세 개의 메서드가 있습니다 `Distance` `DistanceFrom` `DistanceFromXY` .</span><span class="sxs-lookup"><span data-stu-id="a887f-132">The **Point** class contains three methods, `Distance`, `DistanceFrom`, and `DistanceFromXY`.</span></span> <span data-ttu-id="a887f-133">이 세 가지 메서드를 정의 하는 코드 목록은 [사용자 정의 형식 코딩](creating-user-defined-types-coding.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a887f-133">For the code listings defining these three methods, see [Coding User-Defined Types](creating-user-defined-types-coding.md).</span></span>  
  
 <span data-ttu-id="a887f-134">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 `PointValue.Distance` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-134">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement calls the `PointValue.Distance` method:</span></span>  
  
```  
SELECT ID, PointValue.X AS [Point.X],   
    PointValue.Y AS [Point.Y],  
    PointValue.Distance() AS DistanceFromZero   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="a887f-135">결과는 열에 표시 됩니다 `Distance` .</span><span class="sxs-lookup"><span data-stu-id="a887f-135">The results are displayed in the `Distance` column:</span></span>  
  
```  
IDXYDistance  
------------------------  
1345  
2155.09901951359278  
319999.0050503762308  
```  
  
 <span data-ttu-id="a887f-136">`DistanceFrom`메서드는 **point** 데이터 형식의 인수를 사용 하 고 지정 된 점에서 pointvalue 까지의 거리를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-136">The `DistanceFrom` method takes an argument of **Point** data type, and displays the distance from the specified point to the PointValue:</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS Pnt,  
   PointValue.DistanceFrom(CONVERT(Point, '1,99')) AS DistanceFromPoint  
FROM dbo.Points;  
```  
  
 <span data-ttu-id="a887f-137">결과에 테이블의 각 행에 대한 `DistanceFrom` 메서드의 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-137">The results display the results of the `DistanceFrom` method for each row in the table:</span></span>  
  
```  
ID PntDistanceFromPoint  
---------------------  
13,495.0210502993942  
21,594  
31,990  
```  
  
 <span data-ttu-id="a887f-138">`DistanceFromXY` 메서드는 개별적으로 점을 인수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-138">The `DistanceFromXY` method takes the points individually as arguments:</span></span>  
  
```  
SELECT ID, PointValue.X as X, PointValue.Y as Y,   
PointValue.DistanceFromXY(1, 99) AS DistanceFromXY   
FROM dbo.Points  
```  
  
 <span data-ttu-id="a887f-139">결과 집합은 `DistanceFrom` 메서드와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-139">The result set is the same as the `DistanceFrom` method.</span></span>  
  
## <a name="updating-data-in-a-udt-column"></a><span data-ttu-id="a887f-140">UDT 열의 데이터 업데이트</span><span class="sxs-lookup"><span data-stu-id="a887f-140">Updating Data in a UDT Column</span></span>  
 <span data-ttu-id="a887f-141">UDT 열의 데이터를 업데이트하려면 [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-141">To update data in a UDT column, use the [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE statement.</span></span> <span data-ttu-id="a887f-142">UDT의 메서드를 사용하여 개체 상태를 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-142">You can also use a method of the UDT to update the state of the object.</span></span> <span data-ttu-id="a887f-143">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 테이블의 행 하나를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-143">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement updates a single row in the table:</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue = CAST('1,88' AS Point)  
WHERE ID = 3  
```  
  
 <span data-ttu-id="a887f-144">UDT 요소를 개별적으로 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-144">You can also update UDT elements separately.</span></span> <span data-ttu-id="a887f-145">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 Y 좌표만 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-145">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement updates only the Y coordinate:</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue.Y = 99  
WHERE ID = 3  
```  
  
 <span data-ttu-id="a887f-146">바이트 순서를 `true`로 설정하여 UDT가 정의된 경우 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 WHERE 절의 UDT 열을 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-146">If the UDT has been defined with byte ordering set to `true`, [!INCLUDE[tsql](../../includes/tsql-md.md)] can evaluate the UDT column in a WHERE clause.</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue = '4,5'  
WHERE PointValue = '3,4';  
```  
  
### <a name="updating-limitations"></a><span data-ttu-id="a887f-147">업데이트 제한</span><span class="sxs-lookup"><span data-stu-id="a887f-147">Updating Limitations</span></span>  
 <span data-ttu-id="a887f-148">[!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 한 번에 여러 속성을 업데이트할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-148">You cannot update multiple properties at once using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a887f-149">예를 들어 한 UPDATE 문에서 동일한 열 이름을 두 번 사용할 수 없으므로 다음 UPDATE 문은 오류로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-149">For example, the following UPDATE statement fails with an error because you cannot use the same column name twice in one UDATE statement.</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue.X = 5, PointValue.Y = 99  
WHERE ID = 3  
```  
  
 <span data-ttu-id="a887f-150">각 점을 개별적으로 업데이트하려면 Point UDT 어셈블리에 변경자(mutator) 메서드를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-150">To update each point individually, you would need to create a mutator method in the Point UDT assembly.</span></span> <span data-ttu-id="a887f-151">다음과 같이 변경자(mutator) 메서드를 호출하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE 문에서 개체를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-151">You can then invoke the mutator method to update the object in a [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE statement, as in the following:</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue.SetXY(5, 99)  
WHERE ID = 3  
```  
  
## <a name="deleting-data-in-a-udt-column"></a><span data-ttu-id="a887f-152">UDT 열의 데이터 삭제</span><span class="sxs-lookup"><span data-stu-id="a887f-152">Deleting Data in a UDT Column</span></span>  
 <span data-ttu-id="a887f-153">UDT의 데이터를 삭제하려면 [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-153">To delete data in a UDT, use the [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE statement.</span></span> <span data-ttu-id="a887f-154">다음 문은 WHERE 절에 지정된 조건과 일치하는 테이블의 모든 행을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-154">The following statement deletes all rows in the table that match the criteria specified in the WHERE clause.</span></span> <span data-ttu-id="a887f-155">DELETE 문에서 WHERE 절을 생략하면 테이블의 모든 행이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-155">If you omit the WHERE clause in a DELETE statement, all rows in the table will be deleted.</span></span>  
  
```  
DELETE FROM dbo.Points  
WHERE PointValue = CAST('1,99' AS Point)  
```  
  
 <span data-ttu-id="a887f-156">다른 행 값은 그대로 두고 UDT 열의 값을 제거하려면 UPDATE 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-156">Use the UPDATE statement if you want to remove the values in a UDT column while leaving other row values intact.</span></span> <span data-ttu-id="a887f-157">이 예에서는 PointValue를 null로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a887f-157">This example sets the PointValue to null.</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue = null  
WHERE ID = 2  
```  
  
## <a name="see-also"></a><span data-ttu-id="a887f-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a887f-158">See Also</span></span>  
 [<span data-ttu-id="a887f-159">SQL Server의 사용자 정의 형식 작업</span><span class="sxs-lookup"><span data-stu-id="a887f-159">Working with User-Defined Types in SQL Server</span></span>](working-with-user-defined-types-in-sql-server.md)  
  
  
