---
title: 외부 도구에 대한 인수 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- arguments [SQL Server Management Studio]
- external tools [SQL Server Management Studio]
ms.assetid: 3991c13a-f23f-450b-a2ba-19391c399735
author: stevestein
ms.author: sstein
ms.openlocfilehash: 71a7fb99eee3286d21a405e9564d046847406a1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660274"
---
# <a name="arguments-for-external-tools"></a><span data-ttu-id="d4a19-102">Arguments for External Tools</span><span class="sxs-lookup"><span data-stu-id="d4a19-102">Arguments for External Tools</span></span>
  <span data-ttu-id="d4a19-103">인수는 **도구** 메뉴에서 외부 도구가 시작될 때 Studio 환경에서 값을 제공하는 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="d4a19-103">Arguments are variables that the Studio environment supplies values for when an external tool is launched from the **Tools** menu.</span></span> <span data-ttu-id="d4a19-104">**외부 도구** 대화 상자를 사용하여 메모장과 같은 외부 도구를 **도구** 메뉴에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a19-104">External tools such as Notepad can be added to the **Tools** menu using the **External Tools** dialog box.</span></span>  
  
 <span data-ttu-id="d4a19-105">다음 표에서는 외부 도구에 대한 인수를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a19-105">The following table lists arguments for external tools.</span></span>  
  
|<span data-ttu-id="d4a19-106">속성</span><span class="sxs-lookup"><span data-stu-id="d4a19-106">Name</span></span>|<span data-ttu-id="d4a19-107">인수</span><span class="sxs-lookup"><span data-stu-id="d4a19-107">Argument</span></span>|<span data-ttu-id="d4a19-108">Description</span><span class="sxs-lookup"><span data-stu-id="d4a19-108">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="d4a19-109">**항목 경로**</span><span class="sxs-lookup"><span data-stu-id="d4a19-109">**Item Path**</span></span>|<span data-ttu-id="d4a19-110">$(ItemPath)</span><span class="sxs-lookup"><span data-stu-id="d4a19-110">$(ItemPath)</span></span>|<span data-ttu-id="d4a19-111">현재 원본의 전체 파일 이름(드라이브 + 경로 + 파일 이름으로 정의됨)이며 비원본 창이 활성화된 경우에는 비어 있음</span><span class="sxs-lookup"><span data-stu-id="d4a19-111">The complete file name of the current source (defined as drive + path + file name); blank if a non-source window is active.</span></span>|  
|<span data-ttu-id="d4a19-112">**항목 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="d4a19-112">**Item Directory**</span></span>|<span data-ttu-id="d4a19-113">$(ItemDir)</span><span class="sxs-lookup"><span data-stu-id="d4a19-113">$(ItemDir)</span></span>|<span data-ttu-id="d4a19-114">현재 원본의 디렉터리(드라이브 + 경로로 정의됨)이며 비원본 창이 활성화된 경우에는 비어 있음</span><span class="sxs-lookup"><span data-stu-id="d4a19-114">The directory of the current source (defined as drive + path); blank if a non-source window is active.</span></span>|  
|<span data-ttu-id="d4a19-115">**항목 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="d4a19-115">**Item File Name**</span></span>|<span data-ttu-id="d4a19-116">$(ItemFilename)</span><span class="sxs-lookup"><span data-stu-id="d4a19-116">$(ItemFilename)</span></span>|<span data-ttu-id="d4a19-117">현재 원본의 파일 이름(파일 이름으로 정의됨)이며 비원본 창이 활성화된 경우에는 비어 있음</span><span class="sxs-lookup"><span data-stu-id="d4a19-117">The file name of the current source (defined as file name); blank if a non-source window is active.</span></span>|  
|<span data-ttu-id="d4a19-118">**항목 확장명**</span><span class="sxs-lookup"><span data-stu-id="d4a19-118">**Item extension**</span></span>|<span data-ttu-id="d4a19-119">$(ItemExt)</span><span class="sxs-lookup"><span data-stu-id="d4a19-119">$(ItemExt)</span></span>|<span data-ttu-id="d4a19-120">현재 원본의 파일 이름 확장명</span><span class="sxs-lookup"><span data-stu-id="d4a19-120">The file name extension of the current source.</span></span>|  
|<span data-ttu-id="d4a19-121">**현재 줄** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d4a19-121">**Current Line** <sup>1</sup></span></span>|<span data-ttu-id="d4a19-122">$(CurLine)</span><span class="sxs-lookup"><span data-stu-id="d4a19-122">$(CurLine)</span></span>|<span data-ttu-id="d4a19-123">편집기에서 커서의 현재 줄 위치</span><span class="sxs-lookup"><span data-stu-id="d4a19-123">The current line position of the cursor in the editor.</span></span>|  
|<span data-ttu-id="d4a19-124">**현재 열**1</span><span class="sxs-lookup"><span data-stu-id="d4a19-124">**Current Column**1</span></span>|<span data-ttu-id="d4a19-125">$(CurCol)</span><span class="sxs-lookup"><span data-stu-id="d4a19-125">$(CurCol)</span></span>|<span data-ttu-id="d4a19-126">편집기에서 커서의 현재 열 위치</span><span class="sxs-lookup"><span data-stu-id="d4a19-126">The current column position of the cursor in the editor.</span></span>|  
|<span data-ttu-id="d4a19-127">**현재 텍스트**1</span><span class="sxs-lookup"><span data-stu-id="d4a19-127">**Current Text**1</span></span>|<span data-ttu-id="d4a19-128">$(CurText)</span><span class="sxs-lookup"><span data-stu-id="d4a19-128">$(CurText)</span></span>|<span data-ttu-id="d4a19-129">현재 텍스트이며 현재 커서 위치 아래의 단어 또는 단일 줄 선택 영역(있을 경우)</span><span class="sxs-lookup"><span data-stu-id="d4a19-129">The current text (the word under the current cursor position, or a single-line selection, if there is one).</span></span>|  
|<span data-ttu-id="d4a19-130">**대상 경로**</span><span class="sxs-lookup"><span data-stu-id="d4a19-130">**Target Path**</span></span>|<span data-ttu-id="d4a19-131">$(TargetPath)</span><span class="sxs-lookup"><span data-stu-id="d4a19-131">$(TargetPath)</span></span>|<span data-ttu-id="d4a19-132">대상의 전체 파일 이름(드라이브 + 경로 + 파일 이름으로 정의됨)</span><span class="sxs-lookup"><span data-stu-id="d4a19-132">The complete file name of the target (defined as drive + path + file name).</span></span>|  
|<span data-ttu-id="d4a19-133">**대상 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="d4a19-133">**Target Directory**</span></span>|<span data-ttu-id="d4a19-134">$(TargetDir)</span><span class="sxs-lookup"><span data-stu-id="d4a19-134">$(TargetDir)</span></span>|<span data-ttu-id="d4a19-135">대상의 디렉터리</span><span class="sxs-lookup"><span data-stu-id="d4a19-135">The directory of the target.</span></span>|  
|<span data-ttu-id="d4a19-136">**대상 이름**</span><span class="sxs-lookup"><span data-stu-id="d4a19-136">**Target Name**</span></span>|<span data-ttu-id="d4a19-137">$(TargetName)</span><span class="sxs-lookup"><span data-stu-id="d4a19-137">$(TargetName)</span></span>|<span data-ttu-id="d4a19-138">대상의 파일 이름</span><span class="sxs-lookup"><span data-stu-id="d4a19-138">The file name of the target.</span></span>|  
|<span data-ttu-id="d4a19-139">**대상 확장명**</span><span class="sxs-lookup"><span data-stu-id="d4a19-139">**Target Extension**</span></span>|<span data-ttu-id="d4a19-140">$(TargetExt)</span><span class="sxs-lookup"><span data-stu-id="d4a19-140">$(TargetExt)</span></span>|<span data-ttu-id="d4a19-141">대상의 파일 이름 확장명</span><span class="sxs-lookup"><span data-stu-id="d4a19-141">The file name extension of the target.</span></span>|  
|<span data-ttu-id="d4a19-142">**프로젝트 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="d4a19-142">**Project Directory**</span></span>|<span data-ttu-id="d4a19-143">$(ProjDir)</span><span class="sxs-lookup"><span data-stu-id="d4a19-143">$(ProjDir)</span></span>|<span data-ttu-id="d4a19-144">현재 프로젝트의 디렉터리(드라이브 + 경로로 정의됨)</span><span class="sxs-lookup"><span data-stu-id="d4a19-144">The directory of the current project (defined as drive + path).</span></span>|  
|<span data-ttu-id="d4a19-145">**프로젝트 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="d4a19-145">**Project File Name**</span></span>|<span data-ttu-id="d4a19-146">$(ProjFileName)</span><span class="sxs-lookup"><span data-stu-id="d4a19-146">$(ProjFileName)</span></span>|<span data-ttu-id="d4a19-147">현재 프로젝트의 파일 이름(드라이브 + 경로 + 파일 이름으로 정의됨)</span><span class="sxs-lookup"><span data-stu-id="d4a19-147">The file name of the current project (defined as drive + path + file name).</span></span>|  
|<span data-ttu-id="d4a19-148">**솔루션 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="d4a19-148">**Solution Directory**</span></span>|<span data-ttu-id="d4a19-149">$(SolutionDir)</span><span class="sxs-lookup"><span data-stu-id="d4a19-149">$(SolutionDir)</span></span>|<span data-ttu-id="d4a19-150">현재 솔루션의 디렉터리(드라이브 + 경로로 정의됨)</span><span class="sxs-lookup"><span data-stu-id="d4a19-150">The directory of the current solution (defined as drive + path).</span></span>|  
|<span data-ttu-id="d4a19-151">**솔루션 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="d4a19-151">**Solution File Name**</span></span>|<span data-ttu-id="d4a19-152">$(SolutionFileName)</span><span class="sxs-lookup"><span data-stu-id="d4a19-152">$(SolutionFileName)</span></span>|<span data-ttu-id="d4a19-153">현재 솔루션의 파일 이름(드라이브 + 경로 + 파일 이름으로 정의됨)</span><span class="sxs-lookup"><span data-stu-id="d4a19-153">The file name of the current solution (defined as drive + path + file name).</span></span>|  
  
 <span data-ttu-id="d4a19-154"><sup>1</sup> 현재 줄, 현재 열 또는 현재 텍스트는 상태 표시줄에 표시 된 텍스트 편집기의 커서 위치를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a19-154"><sup>1</sup> The current line, current column, or current text is based on the position of the cursor in the text editor as shown in the status bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4a19-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4a19-155">See Also</span></span>  
 <span data-ttu-id="d4a19-156">[외부 도구 대화 상자](external-tools-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="d4a19-156">[External Tools Dialog Box](external-tools-dialog-box.md) </span></span>  
 [<span data-ttu-id="d4a19-157">일반 사용자 인터페이스 요소</span><span class="sxs-lookup"><span data-stu-id="d4a19-157">General User Interface Elements</span></span>](general-user-interface-elements.md)  
  
  
