---
title: 파일 확장명을 코드 편집기에 연결
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- file extensions [SQL Server]
- associating file extensions [SQL Server]
- Query Editor [SQL Server Management Studio], associating file extensions
ms.assetid: 193630f4-93de-4950-8f36-68702531f925
author: rothja
ms.author: jroth
ms.openlocfilehash: 0e8cfbc89892a99971e985ffd3ff10b99f89fe53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649461"
---
# <a name="associate-file-extensions-to-a-code-editor"></a><span data-ttu-id="9a5e6-102">파일 확장명을 코드 편집기에 연결</span><span class="sxs-lookup"><span data-stu-id="9a5e6-102">Associate File Extensions to a Code Editor</span></span>
  <span data-ttu-id="9a5e6-103">파일 확장명을 특정 코드 편집기에 연결하면 Windows 탐색기에서 파일을 두 번 클릭하여 해당 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 코드 편집기에서 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-103">Associating file extensions to a specific code editor allows you to open a file with the appropriate [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] code editor when you double-click a file in Windows Explorer.</span></span> <span data-ttu-id="9a5e6-104">.sql 및 .mdx와 같이 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 많이 사용되는 확장명은 설치 중에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-104">The extensions commonly used by [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], such as .sql and .mdx, are associated during installation.</span></span> <span data-ttu-id="9a5e6-105">새 파일 확장명은 파일 시스템에서 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-105">New file extensions must also be associated to [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] in the file system.</span></span> <span data-ttu-id="9a5e6-106">이 기능을 사용하여 다른 편집기로 만든 파일을 열거나 .sql 파일의 백업인 .bak 파일과 같이 이름이 바뀐 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-106">You can use this feature to open files created with other editors, or to open files you have renamed, such as backups of .sql files that were renamed .bak.</span></span>  
  
 <span data-ttu-id="9a5e6-107">이 과정은 두 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-107">There are two steps in the process.</span></span> <span data-ttu-id="9a5e6-108">먼저 확장명을 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]와 연결한 다음 해당 확장명을 특정 코드 편집기에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-108">First associate the extension with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then associate the extension with a specific code editor.</span></span>  
  
### <a name="to-associate-a-new-file-extension-with-sql-server-management-studio"></a><span data-ttu-id="9a5e6-109">새 파일 확장명을 SQL Server Management Studio와 연결하려면</span><span class="sxs-lookup"><span data-stu-id="9a5e6-109">To associate a new file extension with SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="9a5e6-110">**시작** 메뉴에서 **모든 프로그램**, **보조프로그램**을 차례로 가리키고 **Windows 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-110">On the **Start** menu, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
2.  <span data-ttu-id="9a5e6-111">Windows 탐색기의 **도구** 메뉴에서 **폴더 옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-111">In Windows Explorer, on the **Tools** menu, click **Folder Options**.</span></span>  
  
3.  <span data-ttu-id="9a5e6-112">**폴더 옵션** 대화 상자에서 **파일 형식** 탭을 클릭하고 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-112">In the **Folder Options** dialog box, on the **File Types** tab, click **New**.</span></span>  
  
4.  <span data-ttu-id="9a5e6-113">**새 확장명 만들기** 대화 상자의 **파일 확장명** 상자에 연결하려는 새 파일 확장명을 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-113">In the **Create New Extension** dialog box, in the **File Extension** box, type the new file extension that you want to associate, and then click **OK**.</span></span> <span data-ttu-id="9a5e6-114">확장명 앞에 마침표를 입력하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-114">Do not start the extension with a period.</span></span>  
  
5.  <span data-ttu-id="9a5e6-115">**등록된 파일 형식** 상자에서 새 확장명을 클릭하고 **변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-115">In the **Registered file** types box, click on your new extension, and then click **Change**.</span></span>  
  
6.  <span data-ttu-id="9a5e6-116">**연결 프로그램** 대화 상자에서 **SSMS - SQL Server Management Studio**를 클릭한 다음, **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-116">In the **Open With** dialog box, click **SSMS - SQL Server Management Studio**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="9a5e6-117">**닫기** 를 클릭하여 **폴더 옵션** 대화 상자를 닫은 다음 Windows 탐색기를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-117">Click **Close** to close the **Folder Options** dialog box, and then close Windows Explorer.</span></span>  
  
### <a name="to-associate-a-new-file-extension-with-a-code-editor-in-sql-server-management-studio"></a><span data-ttu-id="9a5e6-118">새 파일 확장명을 SQL Server Management Studio의 코드 편집기와 연결하려면</span><span class="sxs-lookup"><span data-stu-id="9a5e6-118">To associate a new file extension with a code editor in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="9a5e6-119">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-119">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], from the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="9a5e6-120">**옵션** 대화 상자에서 **텍스트 편집기**를 클릭하고 **파일 확장명**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-120">In the **Options** dialog box, click **Text Editor**, and then click **File Extension**.</span></span>  
  
3.  <span data-ttu-id="9a5e6-121">**확장명** 상자에 새 파일 확장명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-121">In the **Extension** box, type your new file extension.</span></span>  
  
4.  <span data-ttu-id="9a5e6-122">**편집기** 상자에서 이 파일 형식을 열 때 사용할 코드 편집기를 클릭하고 **추가**를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9a5e6-122">In the **Editor** box, click the code editor that you wish to use to open this file type, click **Add**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a5e6-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9a5e6-123">See Also</span></span>  
 [<span data-ttu-id="9a5e6-124">Ssms 유틸리티</span><span class="sxs-lookup"><span data-stu-id="9a5e6-124">Ssms Utility</span></span>](../../ssms/ssms-utility.md)  
  
  
