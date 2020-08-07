---
title: 체크 인 한 파일 편집 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying checked-in files
- checking in files
ms.assetid: 560cd19f-ab22-4273-b00c-149993a630e6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e2dbe1aad203dfdc83e438d5b7f4ed19c15038c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732959"
---
# <a name="edit-checked-in-files"></a><span data-ttu-id="19224-102">체크 인 파일 편집</span><span class="sxs-lookup"><span data-stu-id="19224-102">Edit Checked-In Files</span></span>
  <span data-ttu-id="19224-103">일반적으로 원본 제어 파일을 편집하려면 먼저 해당 파일을 체크 아웃해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19224-103">You typically must check out source-controlled files before you can edit them.</span></span> <span data-ttu-id="19224-104">그러나 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 체크 아웃 하지 않은 파일을 수정할 수 있도록를 구성할 수 있습니다. 이렇게 하면 파일을 저장할 때까지 변경 내용이 메모리에 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19224-104">However, you can configure [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] so that you can modify files you have not checked out. When doing so, your changes are held in memory until you save the files.</span></span> <span data-ttu-id="19224-105">그런 다음 소스 제어에서 파일을 체크 아웃하라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="19224-105">You will then be prompted to check out the file from source control.</span></span>  
  
 <span data-ttu-id="19224-106">팀에서 작업하는 중이면 소스 제어 공급자가 로컬 버전 및 서버 버전 체크 아웃을 모두 지원하지 않을 경우에는 체크 인한 파일을 편집할 수 있도록 허용하는 것이 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19224-106">If you work on a team, allowing checked-in files to be edited is not recommended unless your source control provider supports both local version and server version checkouts.</span></span> <span data-ttu-id="19224-107">대부분의 공급자는 로컬 버전 체크 아웃을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19224-107">Most providers do not support local version checkouts.</span></span> <span data-ttu-id="19224-108">공급자가 로컬 버전 체크 아웃을 지원하지 않는 상태에서 체크 인한 파일을 편집하려는 경우 파일을 체크 인하려면 메모리 내 버전과 서버 버전을 수동으로 병합해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19224-108">If your provider does not support local version checkouts and you edit a checked-in file, you have to merge the in-memory and server versions manually before the file can be checked in.</span></span> <span data-ttu-id="19224-109">이 상황에서 자동 및 공급자 지원 병합은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19224-109">Automatic and provider-assisted merges are unsupported in this situation.</span></span>  
  
### <a name="to-edit-checked-in-files"></a><span data-ttu-id="19224-110">체크 인한 파일을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="19224-110">To edit checked-in files</span></span>  
  
1.  <span data-ttu-id="19224-111">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19224-111">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="19224-112">**옵션** 대화 상자에서 **소스 제어**폴더를 확장한 다음 **환경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19224-112">In the **Options** dialog box, expand the **Source Contro**l folder, and then click **Environment**.</span></span>  
  
3.  <span data-ttu-id="19224-113">**체크 인한 항목 편집 허용**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19224-113">Click **Allow checked-in items to be edited**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19224-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="19224-114">See Also</span></span>  
 <span data-ttu-id="19224-115">[체크 인 관리](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="19224-115">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="19224-116">체크 아웃 관리</span><span class="sxs-lookup"><span data-stu-id="19224-116">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
