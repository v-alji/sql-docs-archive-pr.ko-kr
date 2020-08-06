---
title: 기타 파일 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio], miscellaneous
- projects [SQL Server Management Studio], files
- solutions [SQL Server Management Studio], files
- miscellaneous files folder [SQL Server]
ms.assetid: 3c952b0b-8f5f-4d86-9e5d-616c10b9df0d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f65c04326e791fa3684a06213c3042a42f2f2ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733415"
---
# <a name="miscellaneous-files"></a><span data-ttu-id="40678-102">기타 파일</span><span class="sxs-lookup"><span data-stu-id="40678-102">Miscellaneous Files</span></span>
  <span data-ttu-id="40678-103">프로젝트의 외부에 있는 파일을 ‘기타 파일’이라고 합니다. </span><span class="sxs-lookup"><span data-stu-id="40678-103">Files that are external to any project are called *miscellaneous files*.</span></span> <span data-ttu-id="40678-104">솔루션이 열려 있는 경우 프로젝트와 연관된 기타 파일을 열고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40678-104">When you have a solution open, you can open and modify miscellaneous files related to the project.</span></span> <span data-ttu-id="40678-105">파일 확장명이 프로젝트 코드 편집기와 연결되지 않은 경우 파일은 기타 파일로 분류됩니다.</span><span class="sxs-lookup"><span data-stu-id="40678-105">A file is classified as a miscellaneous file if the file extension is not associated with the project code editor.</span></span> <span data-ttu-id="40678-106">예를 들어 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 스크립트 프로젝트에서는 .txt 또는 .mdx 확장명을 가진 파일이 기타 파일로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="40678-106">For example, in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Scripts Project, files with the extension .txt or .mdx will be treated as miscellaneous files.</span></span> <span data-ttu-id="40678-107">MDX 프로젝트에서는 .txt 또는 .sql 확장명을 가진 파일이 기타 파일로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="40678-107">In an MDX project, files with the extension of .txt or .sql will be treated as miscellaneous files.</span></span> <span data-ttu-id="40678-108">파일 확장명을 코드 편집기와 연결 하려면 [파일 확장명을 코드 편집기에 연결](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="40678-108">To associate a file extension with a code editor, see [Associate File Extensions to a Code Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).</span></span>  
  
 <span data-ttu-id="40678-109">기타 파일을 프로젝트에 추가하는 것이 유용한 이유에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40678-109">There are a number of reasons why it is useful to be able to add miscellaneous files to your project.</span></span> <span data-ttu-id="40678-110">인식된 스크립트일 필요는 없지만 솔루션 개발에 필수적인 파일이 존재할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40678-110">You might have a file that is not necessarily a recognized script but integral to the solution's development.</span></span> <span data-ttu-id="40678-111">개발 참고 또는 지침, 데이터 파일, 코드 클립 등을 일반적인 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40678-111">Common examples include development notes or instructions, data files, and code clips.</span></span>  
  
 <span data-ttu-id="40678-112">기타 파일은 유연성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="40678-112">Miscellaneous files provide flexibility.</span></span> <span data-ttu-id="40678-113">예를 들어 데이터베이스에서 테이블과 저장 프로시저를 만들기 위한 여러 스크립트가 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 스크립트 프로젝트가 있다고 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="40678-113">For example, suppose you have a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Scripts Project that has several scripts for creation of tables and stored procedures in your database.</span></span> <span data-ttu-id="40678-114">또한 .BCP 파일 확장명을 가진 테이블에 대한 여러 데이터 파일이 있으며 README.TXT 파일에 실행 지침이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40678-114">You also have several data files for the tables with file extensions .BCP and execution instructions in a README.TXT file.</span></span> <span data-ttu-id="40678-115">이 경우에 프로젝트 시스템의 소스 제어 및 기타 기능을 활용하기 위해 데이터와 README 파일을 기타 파일로 프로젝트에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40678-115">You can attach the data and the README files as miscellaneous files to the project to take advantage of source control and other features of the project system.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="40678-116">메뉴와 도구 모음은 열린 파일의 형식에 따라 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="40678-116">menus and toolbars change according to the format of the file you open.</span></span> <span data-ttu-id="40678-117">예를 들어 텍스트 파일을 열면 텍스트 편집기 도구 모음이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="40678-117">When you open a text file, for example, the Text Editor toolbar appears.</span></span> <span data-ttu-id="40678-118">XML 스키마 파일을 열면 XML 스키마 도구 모음이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="40678-118">If you open an XML Schema file, the XML Schema toolbar appears.</span></span> <span data-ttu-id="40678-119">XML 스키마를 편집하는 동안 텍스트 편집기 도구 모음을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40678-119">While editing your XML Schema, the Text Editor toolbar is unavailable.</span></span> <span data-ttu-id="40678-120">프로젝트 파일과 기타 파일 간에 전환하면 모든 프로젝트 관련 명령과 도구 모음이 기타 파일과 연관된 명령 및 도구 모음으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="40678-120">When you switch between a project file and a miscellaneous file, all project-related commands and toolbars are replaced by those relevant to the miscellaneous file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40678-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40678-121">See Also</span></span>  
 <span data-ttu-id="40678-122">[솔루션 및 프로젝트를 관리 하는 파일](files-that-manage-solutions-and-projects.md) </span><span class="sxs-lookup"><span data-stu-id="40678-122">[Files That Manage Solutions and Projects](files-that-manage-solutions-and-projects.md) </span></span>  
 <span data-ttu-id="40678-123">[솔루션 &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="40678-123">[Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="40678-124">프로젝트&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="40678-124">Projects &#40;SQL Server Management Studio&#41;</span></span>](projects-sql-server-management-studio.md)  
  
  
