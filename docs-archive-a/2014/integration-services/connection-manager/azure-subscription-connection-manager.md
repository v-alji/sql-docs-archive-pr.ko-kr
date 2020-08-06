---
title: Azure 구독 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpsubscrconn.f1
- sql11.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bff1286525983b32c2191f1f8864a0f2bef0e6b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651220"
---
# <a name="azure-subscription-connection-manager"></a><span data-ttu-id="6b982-102">Azure 구독 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="6b982-102">Azure Subscription Connection Manager</span></span>
  <span data-ttu-id="6b982-103">SSIS 패키지는 Azure HDInsight 연결 관리자를 통해 속성에 대해 지정된 값(Azure 구독 ID 및 관리 인증서)을 사용하여 Azure 구독에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b982-103">The Azure HDInsight connection manager enables an SSIS package to connect to an Azure subscription by using the values you specify for the properties: Azure Subscription ID and Management Certificate.</span></span>

1.  <span data-ttu-id="6b982-104">위에 나와 있는 **SSIS 연결 관리자 추가** 대화 상자에서 **Azure 구독**을 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6b982-104">In the **Add SSIS Connection Manager** dialog box shown above, you select **Azure Subscription**, and click **Add**.</span></span>  <span data-ttu-id="6b982-105">다음과 같은 **Azure 구독 연결 관리자 편집기** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b982-105">You should see the following **Azure Subscription Connection Manager Editor** dialog box.</span></span>

     <span data-ttu-id="6b982-106">![SSIS AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "SSIS AzureSubscriptionManager")</span><span class="sxs-lookup"><span data-stu-id="6b982-106">![SSIS-AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "SSIS-AzureSubscriptionManager")</span></span>

2.  <span data-ttu-id="6b982-107">**Azure 구독 ID**에 Azure 구독을 고유하게 식별하는 Azure 구독 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6b982-107">Enter your Azure subscription ID, which uniquely identifies an Azure subscription, for the **Azure subscription ID**.</span></span>  <span data-ttu-id="6b982-108">이 값은 [Azure 관리 포털](https://manage.windowsazure.com) 의 **설정** 페이지에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b982-108">The value can be found on the [Azure Management Portal](https://manage.windowsazure.com) under **Settings** page:</span></span>

     <span data-ttu-id="6b982-109">![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")</span><span class="sxs-lookup"><span data-stu-id="6b982-109">![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")</span></span>

3.  <span data-ttu-id="6b982-110">드롭다운 목록에서 **관리 인증서 저장소 위치** 및 **관리 인증서 저장소 이름** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b982-110">Choose **Management certificate store location** and **Management certificate store name** from the drop-down lists.</span></span>

4.  <span data-ttu-id="6b982-111">**관리 인증서 지문**을 입력하거나 **찾아보기...** 를 클릭하여 선택한 저장소에서 인증서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b982-111">Enter **Management certificate thumbprint** or click the **Browse...** to choose a certificate from the selected store.</span></span> <span data-ttu-id="6b982-112">인증서는 구독용 관리 인증서로 업로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b982-112">The certificate must be uploaded as a management certificate for the subscription.</span></span> <span data-ttu-id="6b982-113">이렇게 하려면 Azure Portal의 다음 페이지에서 **업로드**를 클릭합니다. 자세한 내용은 이 [MSDN 게시물](https://msdn.microsoft.com/library/azure/gg551722.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b982-113">To do so, click **Upload** on the following page of the Azure Portal (see this [MSDN post](https://msdn.microsoft.com/library/azure/gg551722.aspx) for more detail).</span></span>

     <span data-ttu-id="6b982-114">![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")</span><span class="sxs-lookup"><span data-stu-id="6b982-114">![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")</span></span>

5.  <span data-ttu-id="6b982-115">연결 **테스트** 를 클릭 하 여 연결을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b982-115">Click **Test Connection** to test the connection.</span></span>

6.  <span data-ttu-id="6b982-116">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="6b982-116">Click **OK** to close the dialog box.</span></span>


