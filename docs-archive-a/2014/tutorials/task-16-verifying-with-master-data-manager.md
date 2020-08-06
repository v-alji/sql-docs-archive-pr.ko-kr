---
title: '작업 16: 마스터 데이터 관리자을 사용 하 여 확인 Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d1649582f97e9e08691726745e4ba14b2f8226bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732215"
---
# <a name="task-16-verifying-with-master-data-manager"></a><span data-ttu-id="d945c-102">태스크 16: 마스터 데이터 관리자에서 확인</span><span class="sxs-lookup"><span data-stu-id="d945c-102">Task 16: Verifying with Master Data Manager</span></span>
  <span data-ttu-id="d945c-103">이 작업에서는 SSIS 패키지에서 제출된 일괄 처리 작업의 상태를 확인하고 마스터 데이터 관리자를 사용해서 MDS 서버에 데이터가 업로드되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d945c-103">In this task, you check the status of the batch job submitted by the SSIS package and verify that the data was uploaded to MDS server by using Master Data Manager.</span></span>  
  
1.  <span data-ttu-id="d945c-104">**마스터 데이터 관리자** ()를 시작 `http://localhost/MDS` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d945c-104">Launch **Master Data Manager** (`http://localhost/MDS`).</span></span> <span data-ttu-id="d945c-105">이미 열려 있는 경우 맨 위에 있는 **Microsoft SQL Server MDS(Master Data Services)** 를 클릭 하 여 **홈 페이지로**전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d945c-105">If it is already open, click **Microsoft SQL Server Master Data Services** at the top to switch to the **home page**.</span></span>  
  
2.  <span data-ttu-id="d945c-106">**Integration Management**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d945c-106">Click **Integration Management**.</span></span>  
  
3.  <span data-ttu-id="d945c-107">목록에서 제출한 **Eimbatch** 라는 이름의 일괄 처리가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d945c-107">Notice that there is a batch with named **EIMBatch** that you submitted in the list.</span></span> <span data-ttu-id="d945c-108">다음 화면이 표시 되지 않으면 메뉴 모음에서 **데이터 가져오기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d945c-108">Click **Import Data** on the menu bar if you do not see the following screen.</span></span>  
  
     <span data-ttu-id="d945c-109">![EIM Batch](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM Batch")</span><span class="sxs-lookup"><span data-stu-id="d945c-109">![EIM Batch](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM Batch")</span></span>  
  
4.  <span data-ttu-id="d945c-110">맨 위에 있는 **SQL Server 2012 MDS(Master Data Services)** 를 클릭 하 여 홈 페이지로 다시 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d945c-110">Switch back to the home page by click **SQL Server 2012 Master Data Services** at the top.</span></span>  
  
5.  <span data-ttu-id="d945c-111">**모델** 에 대해 **Suppliers** 모델을 선택 하 고 **버전**에 대해 **VERSION_1** 를 선택 했는지 확인 하 고 **탐색기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d945c-111">Make sure that **Suppliers** model is selected for **Model** and **VERSION_1** is selected for **Version**, and click **Explorer**.</span></span>  
  
6.  <span data-ttu-id="d945c-112">MDS로 가져온 데이터 SSIS 패키지를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d945c-112">You can see the data SSIS package imported into MDS.</span></span> <span data-ttu-id="d945c-113">데이터를 정리 하 고 중복 된 **코드** 값을 포함 하지 않아야 합니다 ( **참고: Excel의 공급자 열** 은 MDS의 공급자 엔터티에 대 한 **Code** 특성에 해당).</span><span class="sxs-lookup"><span data-stu-id="d945c-113">The data should be cleansed and have no duplicates **Code** values (Note: **SupplierID** column in Excel corresponds to **Code** attribute of Supplier entity in MDS).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="d945c-114">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d945c-114">Next Step</span></span>  
 [<span data-ttu-id="d945c-115">태스크 17: SSIS 패키지로 생성된 DQS 정리 프로젝트 검토</span><span class="sxs-lookup"><span data-stu-id="d945c-115">Task 17: Reviewing DQS Cleansing Project Created by the SSIS package</span></span>](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
