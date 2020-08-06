---
title: 새 InfoObject 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3587a633-1c0b-4d63-a22a-6b2b93923c3a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 022f2d1e3fe10ae037ea379a02a18845b3a36107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660080"
---
# <a name="create-new-infoobject"></a><span data-ttu-id="d2641-102">새 InfoObject 만들기</span><span class="sxs-lookup"><span data-stu-id="d2641-102">Create New InfoObject</span></span>
  <span data-ttu-id="d2641-103">**새 InfoObject 만들기** 대화 상자를 사용하여 SAP Netweaver BW 시스템에서 새 InfoObject를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-103">Use the **Create New InfoObject** dialog box to create a new InfoObject in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="d2641-104">**InfoObject 만들기** 대화 상자는 **SAP BW 대상 편집기** 의 **연결 관리자**페이지에서 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-104">You can open the **Create InfoObject** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="d2641-105">SAP BW 대상에 대한 자세한 내용은 [SAP BW Destination](sap-bw-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2641-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d2641-106">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="d2641-107">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d2641-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="d2641-108">**새 InfoObject 만들기 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="d2641-108">**To open the Create New InfoObject dialog box**</span></span>  
  
1.  <span data-ttu-id="d2641-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="d2641-110">**데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="d2641-111">**SAP BW 대상 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="d2641-112">**연결 관리자** 페이지의 **SAP BW 개체 만들기** 그룹 상자에서 다음 단계 중 하나를 수행하여 InfoObject를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, do one of the following steps to create an InfoObject:</span></span>  
  
    1.  <span data-ttu-id="d2641-113">InfoObject를 직접 만들려면 **InfoObject**를 선택한 다음 **만들기** 를 클릭하여 **새 InfoObject 만들기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-113">To create an InfoObject directly, select **InfoObject**, and then click **Create** to open the **Create New InfoObject** dialog box.</span></span>  
  
    2.  <span data-ttu-id="d2641-114">InfoCube를 만드는 동안 InfoObject를 만들려면 **InfoCube**를 선택한 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-114">To create an InfoObject while creating an InfoCube, select **InfoCube**, and then click **Create**.</span></span> <span data-ttu-id="d2641-115">**트랜잭션 데이터용 InfoCube 만들기** 대화 상자에 있는 목록의 행 중 하나에 대한 **IObject** 열에서 **만들기** 를 선택하여 **새 InfoObject 만들기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-115">In the **Create InfoCube for Transaction Data** dialog box, in the **IObject** column for one of the rows in the list, select **Create** to open the **Create New InfoObject** dialog box.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d2641-116">테이블의 각 행은 패키지의 데이터 흐름에 있는 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-116">Each row in the table represents a column in the data flow of the package.</span></span>  
  
    3.  <span data-ttu-id="d2641-117">트랜잭션 데이터용 InfoSouce를 만드는 동안 InfoObject를 만들려면 **InfoSource**를 선택한 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-117">To create an InfoObject while creating an InfoSouce for transactional data, select **InfoSource**, and then click **Create**.</span></span> <span data-ttu-id="d2641-118">**InfoSource 만들기** 대화 상자에서 **트랜잭션 데이터**를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-118">In the **Create InfoSource** dialog box, select **Transaction Data**, and then click **OK**.</span></span> <span data-ttu-id="d2641-119">**트랜잭션 데이터용 InfoSource 만들기** 대화 상자에 있는 목록의 행 중 하나에 대한 **IObject** 열에서 **만들기** 를 선택하여 **새 InfoObject 만들기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-119">In the **Create InfoSource for Transaction Data** dialog box, in the **IObject** column for one of the rows in the list, select **Create** to open the **Create New InfoObject** dialog box.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d2641-120">테이블의 각 행은 패키지의 데이터 흐름에 있는 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-120">Each row in the table represents a column in the data flow of the package.</span></span>  
  
    4.  <span data-ttu-id="d2641-121">마스터 데이터용 InfoSource를 만드는 동안 InfoObject를 만들려면 **InfoSource**를 선택한 다음 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-121">To create an InfoObject while creating an InfoSource for master data, select **InfoSource**, and then click **Create**.</span></span> <span data-ttu-id="d2641-122">**InfoSource 만들기** 대화 상자에서 **마스터 데이터**를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-122">In the **Create InfoSource** dialog box, select **Master Data**, and then click **OK**.</span></span> <span data-ttu-id="d2641-123">**마스터 데이터용 InfoSource 만들기** 대화 상자에서 **새로 만들기** 를 클릭하여 **새 InfoObject 만들기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-123">In the **Create InfoSource for Master Data** dialog box, click **New** to open the **Create New InfoObject** dialog box.</span></span>  
  
 <span data-ttu-id="d2641-124">**새 InfoObject 만들기** 대화 상자의 **특성** 섹션에서 **새로 만들기** 를 클릭하여 **새 InfoObject 만들기** 대화 상자를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-124">You can also open the **Create New InfoObject** dialog box by clicking **New** in the **Attributes** section of the **Create New InfoObject** dialog box.</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="d2641-125">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="d2641-125">General Options</span></span>  
 <span data-ttu-id="d2641-126">**특징**</span><span class="sxs-lookup"><span data-stu-id="d2641-126">**Characteristic**</span></span>  
 <span data-ttu-id="d2641-127">차원 데이터를 나타내는 InfoObject를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-127">Create an InfoObject that represents dimension data.</span></span>  
  
 <span data-ttu-id="d2641-128">**주요 수치**</span><span class="sxs-lookup"><span data-stu-id="d2641-128">**Key figure**</span></span>  
 <span data-ttu-id="d2641-129">팩트 데이터를 나타내는 InfoObject를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-129">Create an InfoObject that represents fact data.</span></span>  
  
 <span data-ttu-id="d2641-130">**InfoObject 이름**</span><span class="sxs-lookup"><span data-stu-id="d2641-130">**InfoObject name**</span></span>  
 <span data-ttu-id="d2641-131">InfoObject의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-131">Enter a name for the InfoObject.</span></span>  
  
 <span data-ttu-id="d2641-132">**간단한 설명**</span><span class="sxs-lookup"><span data-stu-id="d2641-132">**Short description**</span></span>  
 <span data-ttu-id="d2641-133">InfoObject에 대한 간단한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-133">Enter a short description for the InfoObject.</span></span>  
  
 <span data-ttu-id="d2641-134">**자세한 설명**</span><span class="sxs-lookup"><span data-stu-id="d2641-134">**Long description**</span></span>  
 <span data-ttu-id="d2641-135">InfoObject에 대한 자세한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-135">Enter a long description for the InfoObject.</span></span>  
  
 <span data-ttu-id="d2641-136">**마스터 데이터 있음**</span><span class="sxs-lookup"><span data-stu-id="d2641-136">**Has master data**</span></span>  
 <span data-ttu-id="d2641-137">InfoObject에 특성, 텍스트 또는 계층의 형태로 마스터 데이터가 포함됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-137">Indicate that the InfoObject contains master data in the form of attributes, texts, or hierarchies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2641-138">InfoObject가 차원 데이터를 나타내고 **특징** 옵션을 선택한 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-138">Select this option if the InfoObject represents dimensional data and you have selected the **Characteristic** option.</span></span>  
  
 <span data-ttu-id="d2641-139">**소문자 허용**</span><span class="sxs-lookup"><span data-stu-id="d2641-139">**Allow lower-case characters**</span></span>  
 <span data-ttu-id="d2641-140">InfoObject 데이터에서 소문자를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-140">Allow lower-case characters in the InfoObject data.</span></span>  
  
 <span data-ttu-id="d2641-141">**저장 및 활성화**</span><span class="sxs-lookup"><span data-stu-id="d2641-141">**Save & Activate**</span></span>  
 <span data-ttu-id="d2641-142">새 InfoObject를 저장하고 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-142">Save and active the new InfoObject.</span></span>  
  
## <a name="data-type-options"></a><span data-ttu-id="d2641-143">데이터 형식 옵션</span><span class="sxs-lookup"><span data-stu-id="d2641-143">Data Type Options</span></span>  
 <span data-ttu-id="d2641-144">**CHAR - 문자열**</span><span class="sxs-lookup"><span data-stu-id="d2641-144">**CHAR - Character String**</span></span>  
 <span data-ttu-id="d2641-145">InfoObject에 문자 데이터가 포함됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-145">Indicates that the InfoObject contains character data.</span></span>  
  
 <span data-ttu-id="d2641-146">**NUMC - 숫자 문자열**</span><span class="sxs-lookup"><span data-stu-id="d2641-146">**NUMC - Numeric String**</span></span>  
 <span data-ttu-id="d2641-147">InfoObject에 숫자 데이터가 포함됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-147">Indicates that the InfoObject contains numeric data.</span></span>  
  
 <span data-ttu-id="d2641-148">**DATS - 날짜(YYYYMMDD)**</span><span class="sxs-lookup"><span data-stu-id="d2641-148">**DATS - Date (YYYYMMDD)**</span></span>  
 <span data-ttu-id="d2641-149">InfoObject에 날짜 데이터가 포함됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-149">Indicates that the InfoObject contains date data.</span></span>  
  
 <span data-ttu-id="d2641-150">**TIMS - 시간(HHMMSS)**</span><span class="sxs-lookup"><span data-stu-id="d2641-150">**TIMS - Time (HHMMSS)**</span></span>  
 <span data-ttu-id="d2641-151">InfoObject에 시간 데이터가 포함됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-151">Indicates that the InfoObject contains time data.</span></span>  
  
 <span data-ttu-id="d2641-152">**길이**</span><span class="sxs-lookup"><span data-stu-id="d2641-152">**Length**</span></span>  
 <span data-ttu-id="d2641-153">데이터의 길이를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-153">Enter the length of the data.</span></span>  
  
## <a name="text-options"></a><span data-ttu-id="d2641-154">텍스트 옵션</span><span class="sxs-lookup"><span data-stu-id="d2641-154">Text Options</span></span>  
 <span data-ttu-id="d2641-155">**텍스트 사용**</span><span class="sxs-lookup"><span data-stu-id="d2641-155">**With Texts**</span></span>  
 <span data-ttu-id="d2641-156">InfoObject에 텍스트가 포함됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-156">Indicate that the InfoObject contains texts.</span></span>  
  
 <span data-ttu-id="d2641-157">**짧은 텍스트**</span><span class="sxs-lookup"><span data-stu-id="d2641-157">**Short Text**</span></span>  
 <span data-ttu-id="d2641-158">InfoObject에 짧은 텍스트가 포함됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-158">Indicates that the InfoObject contains short texts.</span></span>  
  
 <span data-ttu-id="d2641-159">**보통 텍스트**</span><span class="sxs-lookup"><span data-stu-id="d2641-159">**Medium Text**</span></span>  
 <span data-ttu-id="d2641-160">InfoObject에 보통 텍스트가 포함됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-160">Indicates that the InfoObject contains medium texts.</span></span>  
  
 <span data-ttu-id="d2641-161">**긴 텍스트**</span><span class="sxs-lookup"><span data-stu-id="d2641-161">**Long Text**</span></span>  
 <span data-ttu-id="d2641-162">InfoObject에 긴 텍스트가 포함됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-162">Indicates that the InfoObject contains long texts.</span></span>  
  
 <span data-ttu-id="d2641-163">**언어 종속적 텍스트**</span><span class="sxs-lookup"><span data-stu-id="d2641-163">**Text Language-Dependent**</span></span>  
 <span data-ttu-id="d2641-164">텍스트가 언어에 따라 달라짐을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-164">Indicates that the texts are language-dependent.</span></span>  
  
 <span data-ttu-id="d2641-165">**시간 종속적 텍스트**</span><span class="sxs-lookup"><span data-stu-id="d2641-165">**Text Time-Dependent**</span></span>  
 <span data-ttu-id="d2641-166">텍스트가 시간에 따라 달라짐을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-166">Indicates that the texts are time-dependent.</span></span>  
  
## <a name="attributes-section"></a><span data-ttu-id="d2641-167">특성 섹션</span><span class="sxs-lookup"><span data-stu-id="d2641-167">Attributes Section</span></span>  
 <span data-ttu-id="d2641-168">**특성** 섹션은 InfoObject의 특성 목록과 이 목록에서 특성을 추가하고 제거할 수 있는 옵션으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-168">The **Attributes** section consists of a list of attributes for the InfoObject, and the options that let you add and remove attributes from the list.</span></span>  
  
### <a name="attributes-list"></a><span data-ttu-id="d2641-169">특성 목록</span><span class="sxs-lookup"><span data-stu-id="d2641-169">Attributes List</span></span>  
 <span data-ttu-id="d2641-170">**특성** 목록에는 만들고 있는 InfoObject의 특성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-170">The **Attributes** list displays the attributes of the InfoObject that you are creating.</span></span> <span data-ttu-id="d2641-171">**특성** 목록에는 다음과 같은 열 머리글이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-171">The **Attributes** list has the following column headings:</span></span>  
  
 <span data-ttu-id="d2641-172">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="d2641-172">**InfoObject**</span></span>  
 <span data-ttu-id="d2641-173">InfoObject의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-173">View the name of the InfoObject.</span></span>  
  
 <span data-ttu-id="d2641-174">**설명**</span><span class="sxs-lookup"><span data-stu-id="d2641-174">**Description**</span></span>  
 <span data-ttu-id="d2641-175">InfoObject에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-175">View the description of the InfoObject.</span></span>  
  
 <span data-ttu-id="d2641-176">**InfoObject 유형**</span><span class="sxs-lookup"><span data-stu-id="d2641-176">**InfoObject Type**</span></span>  
 <span data-ttu-id="d2641-177">InfoObject의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-177">View the type of the InfoObject.</span></span> <span data-ttu-id="d2641-178">다음 표에서는 유형에 사용할 수 있는 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-178">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="d2641-179">값</span><span class="sxs-lookup"><span data-stu-id="d2641-179">Value</span></span>|<span data-ttu-id="d2641-180">Description</span><span class="sxs-lookup"><span data-stu-id="d2641-180">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d2641-181">CHA</span><span class="sxs-lookup"><span data-stu-id="d2641-181">CHA</span></span>|<span data-ttu-id="d2641-182">특징</span><span class="sxs-lookup"><span data-stu-id="d2641-182">Characteristics</span></span>|  
|<span data-ttu-id="d2641-183">KYF</span><span class="sxs-lookup"><span data-stu-id="d2641-183">KYF</span></span>|<span data-ttu-id="d2641-184">주요 수치</span><span class="sxs-lookup"><span data-stu-id="d2641-184">Key figures</span></span>|  
|<span data-ttu-id="d2641-185">UNI</span><span class="sxs-lookup"><span data-stu-id="d2641-185">UNI</span></span>|<span data-ttu-id="d2641-186">Units</span><span class="sxs-lookup"><span data-stu-id="d2641-186">Units</span></span>|  
|<span data-ttu-id="d2641-187">TIM</span><span class="sxs-lookup"><span data-stu-id="d2641-187">TIM</span></span>|<span data-ttu-id="d2641-188">시간 특징</span><span class="sxs-lookup"><span data-stu-id="d2641-188">Time characteristics</span></span>|  
  
### <a name="attributes-options"></a><span data-ttu-id="d2641-189">특성 옵션</span><span class="sxs-lookup"><span data-stu-id="d2641-189">Attributes Options</span></span>  
 <span data-ttu-id="d2641-190">다음 옵션을 사용하여 만들고 있는 InfoObject의 특성을 추가하고 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-190">Use the following options to add and remove attributes for the InfoObject that you are creating:</span></span>  
  
 <span data-ttu-id="d2641-191">**추가**</span><span class="sxs-lookup"><span data-stu-id="d2641-191">**Add**</span></span>  
 <span data-ttu-id="d2641-192">기존 InfoObject를 특성으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-192">Add an existing InfoObject as an attribute.</span></span>  
  
 <span data-ttu-id="d2641-193">기존 InfoObject를 추가하려면 추가를 클릭한 다음 **InfoObject 조회** 대화 상자를 사용하여 InfoObject를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-193">To add an existing InfoObject, click Add, and then use the **Look Up InfoObject** dialog box to find the InfoObject.</span></span> <span data-ttu-id="d2641-194">이 대화 상자에 대한 자세한 내용은 [Look Up InfoObject](look-up-infoobject.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d2641-194">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="d2641-195">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="d2641-195">**New**</span></span>  
 <span data-ttu-id="d2641-196">새 InfoObject를 특성으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-196">Add a new InfoObject as an attribute.</span></span>  
  
 <span data-ttu-id="d2641-197">새 InfoObject를 만들고 추가하려면 새로 만들기를 클릭한 다음 **새 InfoObject 만들기** 대화 상자의 새 인스턴스를 사용하여 새 InfoObject를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-197">To create and add a new InfoObject, click New, and then use a new instance of the **Create New InfoObject** dialog box to create the new InfoObject.</span></span>  
  
 <span data-ttu-id="d2641-198">**제거**</span><span class="sxs-lookup"><span data-stu-id="d2641-198">**Remove**</span></span>  
 <span data-ttu-id="d2641-199">선택한 InfoObject를 **특성** 목록에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d2641-199">Remove the selected InfoObject from the **Attributes** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2641-200">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2641-200">See Also</span></span>  
 <span data-ttu-id="d2641-201">[트랜잭션 데이터용 InfoCube 만들기](create-infocube-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="d2641-201">[Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md) </span></span>  
 <span data-ttu-id="d2641-202">[InfoSource 만들기](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="d2641-202">[Create InfoSource](create-infosource.md) </span></span>  
 <span data-ttu-id="d2641-203">[트랜잭션 데이터용 InfoSource 만들기](create-infosource-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="d2641-203">[Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) </span></span>  
 <span data-ttu-id="d2641-204">[마스터 데이터용 InfoSource 만들기](create-infosource-for-master-data.md) </span><span class="sxs-lookup"><span data-stu-id="d2641-204">[Create InfoSource for Master Data](create-infosource-for-master-data.md) </span></span>  
 [<span data-ttu-id="d2641-205">Microsoft Connector 1.1 for SAP BW F1 도움말</span><span class="sxs-lookup"><span data-stu-id="d2641-205">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
