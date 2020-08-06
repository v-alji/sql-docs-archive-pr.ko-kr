---
title: Azure Data Lake Store 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSCM.F1
- SQL11.DTS.DESIGNER.AFPADLSCM.F1
ms.assetid: 7f1323f9-9dc3-4378-9c70-bbc65bfeabfd
author: yualan
ms.author: chugu
ms.openlocfilehash: 1ab6e90aad6472cc10bbb12cf4ca17def501bf00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740239"
---
# <a name="azure-data-lake-store-connection-manager"></a><span data-ttu-id="00328-102">Azure Data Lake Store 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="00328-102">Azure Data Lake Store Connection Manager</span></span>
  <span data-ttu-id="00328-103">**Azure Data Lake Store 연결 관리자** 를 사용하면 두 가지 인증 유형 즉, Azure AD 사용자 ID와 Azure AD 서비스 ID를 통해 SSIS 패키지를 Azure Data Lake Store 서비스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00328-103">The **Azure Data Lake Store connection manager** enables an SSIS package to connect to an Azure Data Lake Store service through two authentication types: Azure AD User Identity and Azure AD Service Identity.</span></span>  

## <a name="configure-the-azure-data-lake-store-connection-manager"></a><span data-ttu-id="00328-104">Azure Data Lake Store 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="00328-104">Configure the Azure Data Lake Store Connection Manager</span></span> 
  
1.  <span data-ttu-id="00328-105">**SSIS 연결 관리자 추가** 대화 상자에서 **AzureDataLake**를 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00328-105">In the **Add SSIS Connection Manager** dialog box, select **AzureDataLake**, and click **Add**.</span></span>   
  
2.  <span data-ttu-id="00328-106">Azure Data Lake Store 연결 관리자 편집기 대화 상자에서 **ADLS 호스트** 필드에 Azure Data Lake Store 호스트 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="00328-106">In the Azure Data Lake Store Connection Manager Editor dialog box, type in the Azure Data Lake Store host URL in **ADLS Host** field.</span></span> <span data-ttu-id="00328-107">예: https: \/ /test.azuredatalakestore.net 또는 test.azuredatalakestore.net.</span><span class="sxs-lookup"><span data-stu-id="00328-107">For example: https:\//test.azuredatalakestore.net or test.azuredatalakestore.net.</span></span>
  
3.  <span data-ttu-id="00328-108">해당 인증 유형을 선택하여 Azure Data Lake Store 데이터에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="00328-108">Choose corresponding authentication type to access Azure Data Lake Store data.</span></span>

    1.  <span data-ttu-id="00328-109">**Azure AD 사용자 ID** 인증 옵션을 선택한 경우 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="00328-109">If you selected **Azure AD User Identity** authentication option, do the following:</span></span>

        1. <span data-ttu-id="00328-110">**사용자 이름** 및 **암호** 필드에 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00328-110">Specify values for the **User Name** and **Password** field.</span></span> 
    
        2. <span data-ttu-id="00328-111">**연결 테스트** 단추를 클릭하여 연결을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="00328-111">Click **Test Connection** button to test the connection.</span></span> <span data-ttu-id="00328-112">이전에 사용자 본인과 테넌트 관리자가 Azure Data Lake Store 데이터에 SSIS가 액세스하는 것에 동의하지 않은 경우 팝아웃 대화 상자에서 **동의** 단추를 클릭하여 SSIS가 Azure Data Lake Store 데이터에 액세스하는 것에 동의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00328-112">If you and your tenant administrator didn't consent SSIS to access your Azure Data Lake Store data before, you need click **Accept** button to consent SSIS to access your Azure Data Lake Store data in the pop out dialog.</span></span> <span data-ttu-id="00328-113">이 동의 환경에 대한 자세한 내용은 [Azure Active Directory와 애플리케이션 통합](https://docs.microsoft.com/azure/active-directory/manage-apps/plan-an-application-integration#integrating-applications-with-azure-ad)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00328-113">For more information about this consent experience, see [Integrating applications with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/manage-apps/plan-an-application-integration#integrating-applications-with-azure-ad).</span></span>
    
        > [!NOTE] 
        > <span data-ttu-id="00328-114">Azure AD 사용자 ID 인증 옵션에서는 다단계 인증과 Microsoft 계정이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00328-114">For Azure AD User Identity authentication option, multi-factor authentication and Microsoft account is NOT supported.</span></span>
    
    2.  <span data-ttu-id="00328-115">**Azure AD 서비스 ID** 인증 옵션을 선택한 경우 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="00328-115">If you selected **Azure AD Service Identity** authentication option, do the following:</span></span>
        1. <span data-ttu-id="00328-116">Azure Data Lake 리소스에 액세스할 수 있는 AAD 애플리케이션 및 서비스 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00328-116">Create an AAD application and service principal that can access Azure Data Lake resources.</span></span>
    
        2. <span data-ttu-id="00328-117">이 AAD 애플리케이션에 Azure Data Lake 리소스에 액세스할 수 있는 해당 권한을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="00328-117">Assign this AAD application corresponding permissions to access your Azure Data Lake resources.</span></span> <span data-ttu-id="00328-118">이 인증 옵션에 대한 자세한 내용은 [Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)(리소스에 액세스할 수 있는 Active Directory 애플리케이션 및 서비스 사용자를 포털에서 만들기)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00328-118">For more information about this authentication option, see [Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).</span></span>
    
        3. <span data-ttu-id="00328-119">**클라이언트 ID**, **보안 키** 및 **테넌트 이름** 필드에 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00328-119">Specify values for **Client Id**, **Secret Key** and **Tenant Name** field.</span></span>
    
        4. <span data-ttu-id="00328-120">**연결 테스트** 단추를 클릭하여 연결을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="00328-120">Click **Test Connection** button to test the connection.</span></span>  
  
4.  <span data-ttu-id="00328-121">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="00328-121">Click **OK** to close the dialog box.</span></span>  
  
    <span data-ttu-id="00328-122">작성한 연결 관리자의 속성은 **속성** 창에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00328-122">You can see the properties of the connection manager you created in the **Properties** window.</span></span>  
  
  
