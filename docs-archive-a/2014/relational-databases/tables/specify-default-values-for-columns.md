---
title: 열의 기본값 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], defaults
- default values
ms.assetid: 64514aed-b846-407b-992e-cf813f9a1a91
author: stevestein
ms.author: sstein
ms.openlocfilehash: 650347c29e1175c5a1fe646fc079478520dc8c6d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653753"
---
# <a name="specify-default-values-for-columns"></a><span data-ttu-id="45bdb-102">열의 기본값 지정</span><span class="sxs-lookup"><span data-stu-id="45bdb-102">Specify Default Values for Columns</span></span>
  <span data-ttu-id="45bdb-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 열에 입력되는 기본값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-103">You can specify a default value that will be entered in the column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="45bdb-104">기본값이 지정되지 않은 상태에서 사용자가 열을 빈 채로 두면 다음과 같은 결과가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-104">If you do not assign a default value and the user leaves the column blank, then:</span></span>  
  
-   <span data-ttu-id="45bdb-105">Null 값이 허용되도록 옵션을 설정한 경우 NULL이 열에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-105">If you set the option to allow null values, NULL will be inserted into the column.</span></span>  
  
-   <span data-ttu-id="45bdb-106">Null 값을 허용하는 옵션을 설정하지 않은 경우 열이 빈 채로 남겨지지만 사용자가 열의 값을 입력하지 않으면 행을 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-106">If you do not set the option to allow null values, the column will remain blank, but the user will not be able to save the row until they supply a value for the column.</span></span>  
  
 <span data-ttu-id="45bdb-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="45bdb-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="45bdb-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="45bdb-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="45bdb-109">제한 사항</span><span class="sxs-lookup"><span data-stu-id="45bdb-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="45bdb-110">보안</span><span class="sxs-lookup"><span data-stu-id="45bdb-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="45bdb-111">**기본값을 지정하려면**</span><span class="sxs-lookup"><span data-stu-id="45bdb-111">**To specify a default value, using:**</span></span>  
  
     [<span data-ttu-id="45bdb-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="45bdb-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="45bdb-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="45bdb-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="45bdb-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="45bdb-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="45bdb-115">제한 사항</span><span class="sxs-lookup"><span data-stu-id="45bdb-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="45bdb-116">**기본값** 필드에 값을 입력하여 괄호 없이 표시되는 바인딩된 기본값을 바꾸려는 경우 기본값을 바인딩 해제하고 새 기본값으로 대체하라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-116">If your entry in the **Default Value** field replaces a bound default (which is shown without parentheses), you will be prompted to unbind the default and replace it with your new default.</span></span>  
  
-   <span data-ttu-id="45bdb-117">텍스트 문자열을 입력하려면 값을 작은따옴표(')로 묶어야 합니다. 큰따옴표(")는 따옴표 붙은 식별자용으로 예약되어 있으므로 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-117">To enter a text string, enclose the value in single quotation marks ('); do not use double quotation marks (") because they are reserved for quoted identifiers.</span></span>  
  
-   <span data-ttu-id="45bdb-118">숫자 기본값을 입력하려면 따옴표를 사용하지 않고 숫자를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-118">To enter a numeric default, enter the number without quotation marks around it.</span></span>  
  
-   <span data-ttu-id="45bdb-119">개체/함수를 입력하려면 따옴표 없이 개체/함수의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-119">To enter an object/function, enter the name of the object/function without quotation marks around it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="45bdb-120">보안</span><span class="sxs-lookup"><span data-stu-id="45bdb-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="45bdb-121">권한</span><span class="sxs-lookup"><span data-stu-id="45bdb-121">Permissions</span></span>  
 <span data-ttu-id="45bdb-122">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-122">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="45bdb-123">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="45bdb-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-default-value-for-a-column"></a><span data-ttu-id="45bdb-124">열의 기본값을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="45bdb-124">To specify a default value for a column</span></span>  
  
1.  <span data-ttu-id="45bdb-125">**개체 탐색기**에서 소수 자릿수를 변경할 열이 포함된 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-125">In **Object Explorer**, right-click the table with columns for which you want to change the scale and click **Design**.</span></span>  
  
2.  <span data-ttu-id="45bdb-126">기본값을 지정하려는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-126">Select the column for which you want to specify a default value.</span></span>  
  
3.  <span data-ttu-id="45bdb-127">**열 속성** 탭에서 **기본값 또는 바인딩** 속성에 새 기본값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-127">In the **Column Properties** tab, enter the new default value in the **Default Value or Binding** property.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45bdb-128">숫자 기본값을 입력하려면 숫자를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-128">To enter a numeric default value, enter the number.</span></span> <span data-ttu-id="45bdb-129">개체나 함수의 경우 해당 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-129">For an object or function enter its name.</span></span> <span data-ttu-id="45bdb-130">영숫자 기본값의 경우 원하는 값을 작은따옴표로 묶어 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-130">For an alphanumeric default enter the value inside single quotes.</span></span>  
  
4.  <span data-ttu-id="45bdb-131">**파일** 메뉴에서 ‘테이블 이름’ **저장**을 클릭합니다.__</span><span class="sxs-lookup"><span data-stu-id="45bdb-131">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="45bdb-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="45bdb-132">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-default-value-for-a-column"></a><span data-ttu-id="45bdb-133">열의 기본값을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="45bdb-133">To specify a default value for a column</span></span>  
  
1.  <span data-ttu-id="45bdb-134">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="45bdb-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="45bdb-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45bdb-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    CREATE TABLE dbo.doc_exz ( column_a INT, column_b INT) ;  
    GO  
    INSERT INTO dbo.doc_exz (column_a)VALUES ( 7 ) ;  
    GO  
    ALTER TABLE dbo.doc_exz  
    ADD CONSTRAINT col_b_def  
    DEFAULT 50 FOR column_b ;  
    GO  
  
    ```  
  
 <span data-ttu-id="45bdb-137">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45bdb-137">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
