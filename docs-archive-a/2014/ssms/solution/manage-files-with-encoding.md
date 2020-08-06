---
title: 인코딩으로 파일 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio]
- encoding [SQL Server Management Studio]
- files [SQL Server Management Studio], encoding
ms.assetid: 919544c9-59f0-4cc6-bb2a-f1ad671eb74b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9b0aaa123001fed3f6ad42ea9d642e4007e2640f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661461"
---
# <a name="manage-files-with-encoding"></a><span data-ttu-id="b28be-102">인코딩으로 파일 관리</span><span class="sxs-lookup"><span data-stu-id="b28be-102">Manage Files with Encoding</span></span>
  <span data-ttu-id="b28be-103">특정 언어와 특정 플랫폼에서 코드를 더 쉽게 표시할 수 있도록 특정 문자 인코딩을 파일과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-103">To facilitate the display of your code in a particular language and on a particular platform, you can associate a particular character encoding with a file.</span></span>  
  
## <a name="opening-files"></a><span data-ttu-id="b28be-104">파일 열기</span><span class="sxs-lookup"><span data-stu-id="b28be-104">Opening Files</span></span>  
 <span data-ttu-id="b28be-105">파일을 편집하는 데 사용할 편집기를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-105">You can choose the editor you want to use to edit the file.</span></span>  
  
#### <a name="to-open-a-file-with-a-specific-editor"></a><span data-ttu-id="b28be-106">특정 편집기로 파일을 열려면</span><span class="sxs-lookup"><span data-stu-id="b28be-106">To open a file with a specific editor</span></span>  
  
1.  <span data-ttu-id="b28be-107">**파일** 메뉴에서 **열기**를 가리킨 다음 **파일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-107">On the **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="b28be-108">**파일 열기** 대화 상자에서 파일 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-108">In the **Open File** dialog box, select the file name.</span></span>  
  
3.  <span data-ttu-id="b28be-109">**열기** 단추 옆의 화살표를 클릭한 다음 표시되는 메뉴에서**연결 프로그램** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-109">Click the arrow next to the **Open** button, and then click**Open With** from the menu that appears.</span></span>  
  
4.  <span data-ttu-id="b28be-110">**열려는 프로그램을 선택하십시오.** 목록에서 편집기를 선택한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-110">In the **Select a program to open** list, select an editor, and then click **Open**.</span></span> <span data-ttu-id="b28be-111">특정 인코딩과 함께 파일을 열려면 SQL 쿼리 편집기(인코딩 사용), XML 편집기(인코딩 사용) 등과 같은 인코딩 지원이 포함된 편집기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-111">To open the file with a particular encoding, select an editor with encoding support, such as SQL Query Editor with Encoding or XML Editor with Encoding.</span></span>  
  
## <a name="saving-files"></a><span data-ttu-id="b28be-112">파일 저장</span><span class="sxs-lookup"><span data-stu-id="b28be-112">Saving Files</span></span>  
 <span data-ttu-id="b28be-113">또한 유니코드 인코딩 또는 다른 코드 페이지와 함께 코드를 저장하여 서유럽어 또는 동유럽어와 같은 다양한 언어를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-113">You can also save your code with a Unicode encoding or a different code page to support various languages, such as Western European or Eastern European.</span></span> <span data-ttu-id="b28be-114">특정 문자 인코딩을 파일과 연결하여 해당 언어로 코드를 쉽게 표시할 수 있을 뿐만 아니라 줄 끝 형식과 연결하여 특정 운영 체제를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-114">You can associate a particular character encoding with a file to facilitate the display of your code in that language, as well as a line-ending type to support a particular operating system.</span></span> <span data-ttu-id="b28be-115">또한 일부 문자는 유니코드 인코딩으로 저장하지 않으면 파일 이름에 사용된 경우 이 문자를 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-115">Also, some characters, when used in file names, cannot be saved unless they are saved with Unicode encoding.</span></span>  
  
#### <a name="to-save-a-file-with-a-different-encoding-or-line-ending-type"></a><span data-ttu-id="b28be-116">다른 인코딩 또는 줄 끝 형식으로 파일을 저장하려면</span><span class="sxs-lookup"><span data-stu-id="b28be-116">To save a file with a different encoding or line ending type</span></span>  
  
1.  <span data-ttu-id="b28be-117">**파일** 메뉴에서 **다른 이름으로 \<filename> 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-117">On the **File** menu, click **Save \<filename> As**.</span></span>  
  
2.  <span data-ttu-id="b28be-118">**다른 이름으로 파일 저장** 대화 상자에서 **저장** 단추를 확장한 다음 **인코딩하여 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-118">In the **Save File As** dialog, expand the **Save** button, and then click **Save with Encoding**.</span></span>  
  
3.  <span data-ttu-id="b28be-119">**저장 고급 옵션** 대화 상자의 **인코딩** 목록에서 원하는 인코딩을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-119">In the **Advanced Save Options** dialog box, select the encoding you want from the **Encoding** list.</span></span>  
  
4.  <span data-ttu-id="b28be-120">**줄 끝**목록에서 원하는 줄 끝 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-120">From the **Line Endings**list, select the type of line ending you want.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b28be-121">유니코드 인코딩으로 파일을 저장할 경우 이 파일은 이진 파일로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe에 체크 인되어야 합니다. 이는 유니코드로 저장되는 파일 간의 차이점을 병합, 비교 및 표시하는 기능이 Visual SourceSafe에서 지원되지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-121">If you save your file your file with Unicode encoding, the file should be checked into [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe as a binary file because Visual SourceSafe does not support merging, comparing, and showing differences between files that are saved as Unicode.</span></span>  
  
 <span data-ttu-id="b28be-122">Visual SourceSafe를 사용하여 ANSI, UTF8 또는 유니코드로 파일을 저장하는 경우 각각에 대한 다음 제한 사항에 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="b28be-122">If you are using Visual SourceSafe to store files with ANSI, UTF8, or Unicode, be aware of the following limitations for each:</span></span>  
  
-   <span data-ttu-id="b28be-123">ANSI 파일은 현재 코드 페이지에서 지원되는 문자만 허용하므로 국가별 사용이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-123">ANSI files allow only characters that are supported in the current code page, which limits international use.</span></span>  
  
-   <span data-ttu-id="b28be-124">유니코드 파일은 이진 파일로 처리되므로 공유 체크 아웃, 차이 검사 또는 병합 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-124">Unicode files cannot use shared checkout, difference checking, or merging functionality because they are handled as binary files.</span></span> <span data-ttu-id="b28be-125">국제 범용 파일에서 이 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-125">You can use this format in international files.</span></span>  
  
-   <span data-ttu-id="b28be-126">UTF8 파일의 경우에는 체크 인, 체크 아웃, 차이 검사 및 병합 중에 UTF8 파일 편집기의 문제를 일으키는 변경 내용이 적용되기 때문에 Visual SourceSafe에서 안전하게 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b28be-126">UTF8 files do not work safely with Visual SourceSafe because changes that cause problems for UTF8 file editors are made during check in, check out, difference checking, and merging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b28be-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b28be-127">See Also</span></span>  
 <span data-ttu-id="b28be-128">[솔루션 및 프로젝트를 관리 하는 파일](files-that-manage-solutions-and-projects.md) </span><span class="sxs-lookup"><span data-stu-id="b28be-128">[Files That Manage Solutions and Projects](files-that-manage-solutions-and-projects.md) </span></span>  
 [<span data-ttu-id="b28be-129">파일 확장명을 코드 편집기에 연결</span><span class="sxs-lookup"><span data-stu-id="b28be-129">Associate File Extensions to a Code Editor</span></span>](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)  
  
  
