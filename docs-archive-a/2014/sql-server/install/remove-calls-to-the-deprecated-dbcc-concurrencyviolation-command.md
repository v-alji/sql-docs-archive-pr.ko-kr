---
title: 사용 되지 않는 DBCC CONCURRENCYVIOLATION 명령에 대 한 호출을 제거 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cde04ebfc2ea9996d1c9ed233123e5b66f6e81fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737545"
---
# <a name="remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command"></a><span data-ttu-id="4218c-102">더 이상 사용되지 않는 DBCC CONCURRENCYVIOLATION 명령에 대한 호출을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4218c-102">Remove calls to the deprecated DBCC CONCURRENCYVIOLATION command</span></span>
  <span data-ttu-id="4218c-103">업그레이드 관리자가 DBCC CONCURRENCYVIOLATION 명령 사용을 발견했습니다.</span><span class="sxs-lookup"><span data-stu-id="4218c-103">Upgrade Advisor detected the use of the DBCC CONCURRENCYVIOLATION command.</span></span> <span data-ttu-id="4218c-104">이 명령은 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4218c-104">This command is no longer available.</span></span> <span data-ttu-id="4218c-105">이 명령을 실행하면 오류 2526이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4218c-105">Executing this command returns error 2526.</span></span>  
  
## <a name="component"></a><span data-ttu-id="4218c-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="4218c-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="4218c-107">설명</span><span class="sxs-lookup"><span data-stu-id="4218c-107">Description</span></span>  
 <span data-ttu-id="4218c-108">최신 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 작업 관리자가 없기 때문에 이 명령이 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4218c-108">No recent version of edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] includes a workload governor; therefore the command has been removed.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="4218c-109">수정 동작</span><span class="sxs-lookup"><span data-stu-id="4218c-109">Corrective Action</span></span>  
 <span data-ttu-id="4218c-110">더 이상 사용되지 않는 이 명령에 대한 참조를 제거하도록 애플리케이션과 스크립트를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="4218c-110">Update applications and scripts to remove references to this deprecated command.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="4218c-111">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="4218c-111">External Resources</span></span>  
  
