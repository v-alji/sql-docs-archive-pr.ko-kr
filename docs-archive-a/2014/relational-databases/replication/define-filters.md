---
title: 필터 정의 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.definefilters.f1
helpviewer_keywords:
- Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5154f002c5a35bc78e2eb6777f2cc7bb3d56b635
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646934"
---
# <a name="define-filters"></a><span data-ttu-id="d352f-102">필터 정의</span><span class="sxs-lookup"><span data-stu-id="d352f-102">Define Filters</span></span>
  <span data-ttu-id="d352f-103">**필터 정의** 대화 상자를 사용하여 필터를 정의한 다음 데이터 충돌에 적용하여 충돌의 하위 집합을 표로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d352f-103">The **Define Filters** dialog box allows you to define filters that you then apply to data conflicts to see a subset of the conflicts in the grid.</span></span> <span data-ttu-id="d352f-104">필터를 정의하려면 **연산자** 드롭다운 목록 상자에서 연산자를 선택하고 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d352f-104">To define a filter, choose an operator from the **Operator** drop-down list box and then enter a value.</span></span> <span data-ttu-id="d352f-105">예를 들어 충돌 시 서버 **ReplTest1**의 변경 내용이 무시되는 충돌만 표시하려면 **연산자** 드롭다운 목록 상자에서 **같음** 을 선택하고 첫 번째 **값** 열에 **ReplTest1** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d352f-105">For example, to show only those conflicts in which the conflict loser is server **ReplTest1**, select **Equal to** from the **Operator** drop-down list box and enter **ReplTest1** in the first **Value** column.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d352f-106">옵션</span><span class="sxs-lookup"><span data-stu-id="d352f-106">Options</span></span>  
 <span data-ttu-id="d352f-107">**연산자**</span><span class="sxs-lookup"><span data-stu-id="d352f-107">**Operator**</span></span>  
 <span data-ttu-id="d352f-108">**작거나 같음**등의 필터에 대한 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d352f-108">Select an operator for the filter, such as **Less than or Equal to**.</span></span>  
  
 <span data-ttu-id="d352f-109">**값**</span><span class="sxs-lookup"><span data-stu-id="d352f-109">**Value**</span></span>  
 <span data-ttu-id="d352f-110">필터 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d352f-110">Enter a value for the filter.</span></span> <span data-ttu-id="d352f-111">대부분의 연산자는 첫 번째 **값** 열에만 값을 입력하면 되지만 **사이** 및 **사이에 있지 않음** 연산자는 두 **값** 열에 값을 모두 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d352f-111">Most operators only require a value in the first **Value** column, but the **Between** and **Not Between** operators require a value in both of the **Value** columns.</span></span>  
  
 <span data-ttu-id="d352f-112">**지우기**</span><span class="sxs-lookup"><span data-stu-id="d352f-112">**Clear**</span></span>  
 <span data-ttu-id="d352f-113">이 단추를 클릭하여 이전에 정의한 필터를 모두 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d352f-113">Click this button to clear all filters that have been previously defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d352f-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d352f-114">See Also</span></span>  
 <span data-ttu-id="d352f-115">[Microsoft 복제 충돌 뷰어&#40;병합 복제&#41;](microsoft-replication-conflict-viewer-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="d352f-115">[Microsoft Replication Conflict Viewer &#40;Merge Replication&#41;](microsoft-replication-conflict-viewer-merge-replication.md) </span></span>  
 [<span data-ttu-id="d352f-116">Microsoft 복제 충돌 뷰어&#40;트랜잭션 복제&#41;</span><span class="sxs-lookup"><span data-stu-id="d352f-116">Microsoft Replication Conflict Viewer &#40;Transactional Replication&#41;</span></span>](microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
