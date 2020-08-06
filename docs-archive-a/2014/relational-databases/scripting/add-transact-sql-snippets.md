---
title: Transact-SQL 코드 조각 추가
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 901c7995-8eb5-4d12-8bb0-de0a922b48f8
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b5886f8f36ae3753fcb7c89dd3aeff9c69eeba5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649464"
---
# <a name="add-transact-sql-snippets"></a><span data-ttu-id="45262-102">Transact-SQL 코드 조각 추가</span><span class="sxs-lookup"><span data-stu-id="45262-102">Add Transact-SQL Snippets</span></span>
  <span data-ttu-id="45262-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 포함된 미리 정의된 코드 조각 집합에 사용자 고유의 Transact-SQL 코드 조각을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45262-103">You can add your own Transact-SQL code snippets to the set of pre-defined snippets included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="creating-a-transact-sql-snippet-file"></a><span data-ttu-id="45262-104">Transact-SQL 코드 조각 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="45262-104">Creating a Transact-SQL Snippet File</span></span>  
 <span data-ttu-id="45262-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] 코드 조각을 만드는 첫 번째 단계는 사용자 코드 조각의 텍스트가 포함된 XML 파일을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="45262-105">The first part of creating a [!INCLUDE[tsql](../../includes/tsql-md.md)] code snippet is to create an XML file with the text of your code snippet.</span></span> <span data-ttu-id="45262-106">이 파일은 파일 확장명이 .snippet이고 [코드 조각 스키마](https://go.microsoft.com/fwlink/?LinkId=207504)의 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-106">The file must have a .snippet file extension, and meet the requirements of the [Code Snippets Schema](https://go.microsoft.com/fwlink/?LinkId=207504).</span></span> <span data-ttu-id="45262-107">코드 조각 언어는 SQL로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-107">Set the snippet language to SQL.</span></span>  
  
 <span data-ttu-id="45262-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 함께 제공되는 미리 정의된 코드 조각을 예로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45262-108">You can use the pre-defined snippets that ship with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as examples.</span></span> <span data-ttu-id="45262-109">미리 정의된 코드 조각을 찾으려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 열고 **도구** 메뉴를 선택한 다음 **코드 조각 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-109">To find the pre-defined snippets, open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the **Tools** menu, and click **Code Snippet Manager**.</span></span> <span data-ttu-id="45262-110">**언어** 목록 상자에서 **SQL** 을 선택하면 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드 조각의 경로가 **위치** 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="45262-110">Select **SQL** in the **Language** list box, the path to the [!INCLUDE[tsql](../../includes/tsql-md.md)] snippets is displayed in the **Location** box.</span></span>  
  
## <a name="registering-the-code-snippet"></a><span data-ttu-id="45262-111">코드 조각 등록</span><span class="sxs-lookup"><span data-stu-id="45262-111">Registering the Code Snippet</span></span>  
 <span data-ttu-id="45262-112">코드 조각 파일을 만든 후에는 코드 조각 관리자를 사용하여 코드 조각을 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-112">After creating the snippet file, use the Code Snippets Manager to register the snippet with [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="45262-113">여러 코드 조각이 들어 있는 폴더를 추가하거나 개별 코드 조각을 **내 코드 조각** 폴더로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45262-113">You can either add a folder containing multiple snippets, or import individual snippets to the **My Code Snippets** folder.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="45262-114">프로시저</span><span class="sxs-lookup"><span data-stu-id="45262-114">Procedures</span></span>  
  
#### <a name="adding-a-snippet-folder"></a><span data-ttu-id="45262-115">코드 조각 폴더 추가</span><span class="sxs-lookup"><span data-stu-id="45262-115">Adding a Snippet Folder</span></span>  
  
1.  <span data-ttu-id="45262-116">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="45262-116">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="45262-117">**도구** 메뉴를 선택하고 **코드 조각 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-117">Select the **Tools** menu, and click **Code Snippets Manager**.</span></span>  
  
3.  <span data-ttu-id="45262-118">**추가** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-118">Click the **Add** button.</span></span>  
  
4.  <span data-ttu-id="45262-119">코드 조각이 들어 있는 폴더로 이동하고 **폴더 선택** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-119">Navigate to the folder containing your code snippets, and click the **Select Folder** button.</span></span>  
  
#### <a name="importing-a-snippet"></a><span data-ttu-id="45262-120">코드 조각 가져오기</span><span class="sxs-lookup"><span data-stu-id="45262-120">Importing a Snippet</span></span>  
  
1.  <span data-ttu-id="45262-121">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="45262-121">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="45262-122">**도구** 메뉴를 선택하고 **코드 조각 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-122">Select the **Tools** menu, and click **Code Snippets Manager**.</span></span>  
  
3.  <span data-ttu-id="45262-123">**가져오기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-123">Click the **Import** button.</span></span>  
  
4.  <span data-ttu-id="45262-124">코드 조각이 들어 있는 폴더로 이동하고 .snippet 파일을 클릭한 다음 **열기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-124">Navigate to the folder containing your snippet, click on the .snippet file, and click the **Open** button.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="45262-125">예</span><span class="sxs-lookup"><span data-stu-id="45262-125">Examples</span></span>  
 <span data-ttu-id="45262-126">다음 예에서는 `TRY-CATCH` 코드 감싸기 조각을 만들어 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="45262-126">The following example creates a `TRY-CATCH` surround-with snippet and imports it to [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
1.  <span data-ttu-id="45262-127">다음 코드를 메모장에 붙여 넣은 다음 TryCatch.snippet이라는 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-127">Paste the following code into notepad, then save as a file named TryCatch.snippet.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CodeSnippets  xmlns="https://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <_locDefinition xmlns="urn:locstudio">  
        <_locDefault _loc="locNone" />  
        <_locTag _loc="locData">Title</_locTag>  
        <_locTag _loc="locData">Description</_locTag>  
        <_locTag _loc="locData">Author</_locTag>  
        <_locTag _loc="locData">ToolTip</_locTag>  
       <_locTag _loc="locData">Default</_locTag>  
    </_locDefinition>  
    <CodeSnippet Format="1.0.0">  
    <Header>  
    <Title>TryCatch</Title>  
                            <Shortcut></Shortcut>  
    <Description>Example Snippet for Try-Catch.</Description>  
    <Author>SQL Server Books Online Example</Author>  
    <SnippetTypes>  
                                    <SnippetType>SurroundsWith</SnippetType>  
    </SnippetTypes>  
    </Header>  
    <Snippet>  
    <Declarations>  
                                    <Literal>  
                                    <ID>CatchCode</ID>  
                                    <ToolTip>Code to handle the caught error</ToolTip>  
                                    <Default>CatchCode</Default>  
                                    </Literal>  
    </Declarations>  
    <Code Language="SQL"><![CDATA[  
    BEGIN TRY  
  
    $selected$ $end$  
  
    END TRY  
    BEGIN CATCH  
  
    $CatchCode$  
  
    END CATCH;  
    ]]>  
    </Code>  
    </Snippet>  
    </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
2.  <span data-ttu-id="45262-128">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="45262-128">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
3.  <span data-ttu-id="45262-129">**도구** 메뉴를 선택하고 **코드 조각 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-129">Select the **Tools** menu, and click **Code Snippets Manager**.</span></span>  
  
4.  <span data-ttu-id="45262-130">**가져오기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-130">Click the **Import** button.</span></span>  
  
5.  <span data-ttu-id="45262-131">TryCatch.snippet이 들어 있는 폴더로 이동하고 TryCatch.snippet 파일을 클릭한 다음 **열기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-131">Navigate to the folder containing TryCatch.snippet, click on the TryCatch.snippet file, and click the **Open** button.</span></span> <span data-ttu-id="45262-132">**내 코드 조각** 폴더에 TryCatch 코드 조각이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45262-132">You should not have a TryCatch snippet in your **My Code Snippets** folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45262-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45262-133">See Also</span></span>  
 [<span data-ttu-id="45262-134">코드 감싸기 Transact-SQL 조각 삽입</span><span class="sxs-lookup"><span data-stu-id="45262-134">Insert Surround-with Transact-SQL snippets</span></span>](insert-surround-with-transact-sql-snippets.md)  
  
  
