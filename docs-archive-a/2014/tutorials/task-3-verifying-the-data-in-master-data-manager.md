---
title: '작업 3: 마스터 데이터 관리자에서 데이터 확인 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d88953d2-2258-40ac-b3bf-2ef502f9b5fd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: aed5a76cff9d90b81f02f6af11b6fc437efee14e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647376"
---
# <a name="task-3-verifying-the-data-in-master-data-manager"></a><span data-ttu-id="9f38f-102">태스크 3: 마스터 데이터 관리자에서 데이터 확인</span><span class="sxs-lookup"><span data-stu-id="9f38f-102">Task 3: Verifying the Data in Master Data Manager</span></span>
  <span data-ttu-id="9f38f-103">이 작업에서는 **마스터 데이터 관리자 웹 애플리케이션** 을 사용해서 **Supplier** 엔터티가 **MDS**에 생성되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9f38f-103">In this task, you verify that the **Supplier** entity is created on **MDS** using **Master Data Manager Web Application**.</span></span>

1.  <span data-ttu-id="9f38f-104">**마스터 데이터 관리자** 가 이미 열려 있으면 상단에서 **SQL Server 2012 Master Data Services** 를 클릭하여 홈 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="9f38f-104">If **Master Data Manager** is already open, click **SQL Server 2012 Master Data Services** at the top to navigate to the home page.</span></span> <span data-ttu-id="9f38f-105">그렇지 않으면로 이동 `http://localhost/MDS` 하 여 **마스터 데이터 관리자**를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f38f-105">Otherwise, navigate to `http://localhost/MDS` to launch **Master Data Manager**.</span></span>

2.  <span data-ttu-id="9f38f-106">**모델** 에 대해 **Suppliers**를 선택하고 **탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f38f-106">Select **Suppliers** for **Model**, and click **Explorer**.</span></span>

     <span data-ttu-id="9f38f-107">![마스터 데이터 관리자 - 탐색기 단추](../../2014/tutorials/media/et-verifyingthedatainmasterdatamanager.jpg "마스터 데이터 관리자 - 탐색기 단추")</span><span class="sxs-lookup"><span data-stu-id="9f38f-107">![Master Data Manager - Explorer Button](../../2014/tutorials/media/et-verifyingthedatainmasterdatamanager.jpg "Master Data Manager - Explorer Button")</span></span>

3.  <span data-ttu-id="9f38f-108">MDS에 저장된 데이터를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="9f38f-108">Review the data stored on MDS.</span></span> <span data-ttu-id="9f38f-109">데이터가 표시되지 않으면 **탐색기** 를 실행하기 전에 홈 페이지에서 **모델** 에 대해 **Suppliers**를 선택했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9f38f-109">If you do not see the data, confirm that you selected **Suppliers** for the **Model** on the home page before launching **Explorer**.</span></span> <span data-ttu-id="9f38f-110">도구 모음에서 **멤버 추가** 및 **멤버 삭제** 단추를 사용하여 공급자 목록에서 멤버를 추가하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f38f-110">You can add to or delete from the supplier list by using **Add Member** and **Delete Member** buttons on the toolbar.</span></span>

## <a name="next-step"></a><span data-ttu-id="9f38f-111">다음 단계</span><span class="sxs-lookup"><span data-stu-id="9f38f-111">Next Step</span></span>
 [<span data-ttu-id="9f38f-112">작업 4 &#40;선택적&#41;: 새 데이터 집합 결합, 일치 및 게시</span><span class="sxs-lookup"><span data-stu-id="9f38f-112">Task 4 &#40;Optional&#41;: Combining, Matching, and Publishing New Set of Data</span></span>](../../2014/tutorials/task-4-optional-combining-matching-and-publishing-new-set-of-data.md)


